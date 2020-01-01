# Introduction

As the name implies, extensions serve to "extend" the capabilities of BeEF. Extensions differ slightly from modules. They are a way to add new functionality to the core features of BeEF whereas modules usually have a narrow set of abilities that perform a specific task. This helps prevent feature creep by modularizing new core features. So if you're asking yourself...

### "I have a new idea, should it be a module or an extension?"

Does it change the way BeEF behaves? ___Extension___

Does it change the way zombies behave? ___Module___

# Directory Layout

So you've decided to add a new extension. Great but where should it go? Extensions are housed in the `extensions/` directory and will generally have the following layout:

* `extension.rb`
* `<name>.rb`
* `config.yaml`
* `api.rb`
* `model.rb`
* `rest/`
   + `<name>.rb`

Technically, the only required files are `extension.rb` and `config.yaml`. In practice though, you'll also want a `<name>.rb` file at the very least so that everything isn't crammed into one place. Sticking to this layout allows for increased consistency and maintainability.

* `extension.rb`  
This file is the main entry point of an extension. When BeEF loads its extensions as it boots, this is where it will start. Its contents consists of the metadata related to your extension: its short name, full name, and description. It is also where you will `require` any other files used by your extension. The class defined here must extend `BeEF::API::Extension`.

* `<name>.rb`  
This is where the core functionality of your extension will go. It will fall under the `BeEF::Extension` namespace. For example, if your extension is called "foobar", this file will be named `foobar.rb` and will define the module `BeEF::Extension::Foobar`. If you find that your extension requires more than just a single class, you should split it up into multiple files.

* `config.yaml`  
Any extension-specific settings will be found here. Your extension name must fall under `beef.extension` and at the very least, contain a boolean key `enable` for controlling its use.

* `api.rb`  
If an extension needs to register any timed API calls, this is where you would define a class that does so. The most common API class to hook into is `BeEF::API::Server` for registering `#pre_http_start` and `#mount_handler`. If you require multiple classes, place them under a new `api/` subdirectory.

* `model.rb`  
If an extension requires a database model, this is where the model is defined. BeEF uses [DataMapper](http://datamapper.org) as its ORM so any class defined here must mixin `DataMapper::Resource`. If you require multiple models, place them under a new `models/` subdirectory.

* `rest/`  
Extensions that add to BeEF's RESTful API interface will do so in this subdirectory. The associated HTTP routes are defined using [Sinatra](http://www.sinatrarb.com) inside `<name>.rb`.

# Daytime Example

Imagine that you're reading BeEF's [issue tracker](https://github.com/beefproject/beef/issues) and stumble upon a module request. For whatever reason, this particular module requires access to the Daytime protocol. As an expert BeEF hacker, you decide the best way to implement the Daytime service is as an extension. That way, this module or any future modules and extensions need only to contact the BeEF server should they require the Daytime service.

Begin by creating a new `extensions/daytime/` directory. In it, the first two files you'll need are `extension.rb` and `config.yaml`.

```ruby
# extension.rb
module BeEF
module Extension
module Daytime

  extend BeEF::API::Extension

  @short_name  = 'daytime'
  @full_name   = 'Daytime Service'
  @description = 'Implementation of the Daytime protocol which sends the current date and time'

end
end
end

require 'extensions/daytime/api.rb'
require 'extensions/daytime/daytime.rb'
```

This class should be pretty straightfoward. All that's needed is to extend `BeEF::API::Extension` and define `@short_name`, `@full_name`, and `@description` for explaining the short name, full name, and description of your extension respectively. At the end of the file, you'll want to `require` any other source files. Here we've included `api.rb` and `daytime.rb`. We haven't defined them yet but we will soon.

You're halfway there. Now write your `config.yaml` file.

```yaml
# config.yaml
beef:
    extension:
        daytime:
            enable: true
            name: 'Daytime Service'
            address: '127.0.0.1'
            port: '1300'
            authors: ['Kilgore Trout']
```

Since we're writing a really simple extension, only a few basic settings are needed in `config.yaml`. The `enable` key is used to control whether or not the extension should be loaded and `name` should be something similar to `@full_name` in `extension.rb`. The address and port of the server are defined in, you guessed it, `address` and `port`. Notice that we've set the port to 1300 instead of the traditional port 13. This is because well-known ports 0-1023 require superuser privileges. Lastly, the `authors` key is for crediting this awesome work to yourself.

## Bringing Things to Life

Time to give this extension some character. Create a new `daytime.rb` file like so.

```ruby
# daytime.rb
module BeEF
module Extension
module Daytime

  class Server

    FORMAT = "%A, %B %d, %Y %H:%M:%S-%Z"

    def self.run_server(address, port)
      @server = TCPServer.new(address, port)
      
      loop do
        Thread.start(@server.accept) do |socket|
          socket.write(Time.now.strftime(FORMAT))
          socket.close
        end
      end
    end

  end

end
end
end
```

Pretty simple, right? This is your basic socket server. On a new connection request, it simply uses Ruby's `Time` class to send back the current time.

What you do in your extension is entirely up to you. There is no restriction other than that it be defined under `BeEF::Extension`.

But how do we get it to run when BeEF starts up? This is where BeEF's API registrar comes into play. When BeEF starts, it runs any methods that have hooked `BeEF::API::Server#pre_http_start`. That's exactly what we'll do in `api.rb`.

```ruby
# api.rb
module BeEF
module Extension
module Daytime
module API

  module DaytimeHandler
  
    BeEF::API::Registrar.instance.register(BeEF::Extension::Daytime::API::DaytimeHandler,
                                           BeEF::API::Server,
                                           'pre_http_start')
  
    def self.pre_http_start(http_hook_server)
      config = BeEF::Core::Configuration.instance
      
      address = config.get('beef.extension.daytime.address')
      port = config.get('beef.extension.daytime.port')
      
      Thread.new { BeEF::Extension::Daytime::Server.run_server(address, port) }
      
      print_info "Daytime Server: #{address}:#{port}"
    end
  
  end

end
end
end
end
```

To register our `#pre_http_start` method with BeEF, we inform the registrar via the call to `BeEF::API::Registrar#register.` Inside `#pre_http_start` we retrieve the address and port values from the config file using `BeEF::Core::Configuration`. Notice that we started our server inside a new thread. This is because our extension is meant to run continuosly in the background. If we hadn't, BeEF would continue waiting for `#pre_http_start` to return and eventually end up hanging indefinitely.

## In Action

Now that the server has been implemented and we've told BeEF when to start it, we can check that everything is in place by running BeEF.

```
[foobar@localhost beef]$ ./beef
[21:43:34][*] Bind socket [imapeudora1] listening on [0.0.0.0:2000].
[21:43:34][*] Browser Exploitation Framework (BeEF) 0.4.4.5-alpha
[21:43:34]    |   Twit: @beefproject
[21:43:34]    |   Site: http://beefproject.com
[21:43:34]    |   Blog: http://blog.beefproject.com
[21:43:34]    |_  Wiki: https://github.com/beefproject/beef/wiki
[21:43:34][*] Project Creator: Wade Alcorn (@WadeAlcorn)
[21:43:35][*] BeEF is loading. Wait a few seconds...
[21:43:35][*] 13 extensions enabled.
[21:43:35][*] 162 modules enabled.
[21:43:35][*] 2 network interfaces were detected.
[21:43:35][+] running on network interface: 127.0.0.1
[21:43:35]    |   Hook URL: http://127.0.0.1:3000/hook.js
[21:43:35]    |_  UI URL:   http://127.0.0.1:3000/ui/panel
[21:43:35][+] running on network interface: 192.168.240.28
[21:43:35]    |   Hook URL: http://192.168.240.28:3000/hook.js
[21:43:35]    |_  UI URL:   http://192.168.240.28:3000/ui/panel
[21:43:35][*] RESTful API key: 1e95497768c5aa542eb2632362869ec050e48142
[21:43:35][*] Daytime Server: 127.0.0.1:1300
[21:43:35][*] HTTP Proxy: http://127.0.0.1:6789
[21:43:35][*] BeEF server started (press control+c to stop)
```

Tada! Right near the bottom, you'll see that our extension was loaded properly. This doesn't necessarily mean our Daytime server actually works though so let's use Netcat just to make sure.

```
[foobar@localhost ~]$ nc 127.0.0.1 1300
Sunday, June 09, 2013 21:50:52-EDT
```

No problems here.

# Moving Forward

Our Daytime server was just a simple way to show the structure and layout of extensions. In reality, it's unlikely that BeEF would ever actually need it. If you feel comfortable with everything so far, a good way to move forward is to learn from the host of already existing extensions in the `extensions/` directory. Sometimes the best way to learn is by example.

***
[[Advanced Module Creation|Advanced Module Creation]] | [[BeEF Testing|BeEF Testing]]
