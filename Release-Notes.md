# Release Notes

***

## 0.5.2.0

### Core - Fixed public hook url configuration settings (#1785)

As mentioned in #1785 there is currently a bug that prevents BeEF from hooking browsers when the BeEF hook (public) URL is different from the BeEF host (local) URL ((ie, behind a reverse proxy, or when used via services such as ngrok, or when using port forwarding from a border gateway)

To resolve this issue the PR completely decouples the local host settings from the public settings.
This means that if a user sets anything in the public section within the configuration.

```YAM
        # If BeEF is running behind a reverse proxy or NAT
        #  set the public hostname and port here & protocol
        public:
            host: "example.com"
            port: "3000"
            https: true/false
```

It will automatically use these values when referencing the hook (public) URL.
These values can be seen in the Configuration object used through the application.

#### Beef Host
```Ruby
      #
       # Returns the beef host which is used by external resources
       # e.g. hooked browsers
       def beef_host
         public_host || local_host
       end
```
#### Beef Port
```Ruby
      #
       # Returns the beef port which is used by external resource
       # e.g. hooked browsers
       def beef_port
         public_port || local_port
       end
```

#### Beef protocol (http/https)
```Ruby
#
       # Returns the beef protocol that is used by external resources
       # e.g. hooked browsers
       def beef_proto
         if public_enabled? && public_https_enabled? then
           return 'https'
         elsif public_enabled? && !public_https_enabled?
           return 'http'
         elsif !public_enabled?
           return local_proto
         end
       end
```

A contributor can now new some new configuration values that will reference the full hooking url

```Ruby
      #
       # Returns the beef scheme://host:port for external resources
       # e.g. hooked browsers
       def beef_url_str
         "#{beef_proto}://#{beef_host}:#{beef_port}"
       end

      # Returns the url to the hook file
       #
       # @return [String] the url string
       def hook_url
         "#{beef_url_str}#{hook_file_path}"
       end
```

These new configuration getters can be used through the code base reducing the code repetition found through the code base

```Ruby    
     @configuration = BeEF::Core::Configuration.instance
     beef_proto = @configuration.get("beef.http.https.enable") == true ? "https" : "http";
     beef_host = @configuration.get("beef.http.public") || @configuration.get("beef.http.host")
     beef_port = @configuration.get("beef.http.public_port") || @configuration.get("beef.http.port")
     beef_hook = @configuration.get("beef.http.hook_file")
     hook_url = "#{beef_proto}://#{beef_host}:#{beef_port}/#{beef_hook}"
```

Can now simply be the following

```Ruby
    @config.hook_url
```

The most common issue that would be raised due to this bug was when a users was trying to implement ngrok.
Ngrok would use the https protocol and if the user did not setup the beef local host using https it would cause mixed content errors preventing browser hooking.

With the net configuration items, the user can now have a https proxy that redirects to a http local host, please see the new setup instructions for ngrok [here](https://github.com/beefproject/beef/wiki/FAQ#how-do-i-configure-beef-with-ngrok)

### Fixed - Cannot delete offline hook browsers (#2044)
Extension: Admin UI

Currently there is a defect if an offline zombie exists and you try to delete it in the tree list view, it will not delete.
This was due to the existing code not referencing the correct variable for online/offline hooked browser

![Screen Shot 2021-09-12 at 8 59 09 am](https://user-images.githubusercontent.com/689558/132963657-95dd2563-3a8a-44cb-832b-02a8c04388a9.png)

```Javascript
  var hb_id = this.contextNode.id.split('zombie-online-')[1];
  var hb_id_off = this.contextNode.id.split('zombie-offline-')[1];
```

The code used to delete the zombie referenced the hb_id

```Javascript
  var token = beefwui.get_rest_token();
  if (!confirm('Are you sure you want to delete zombie [id: ' + hb_id + '] ?\nWarning: this will remove all zombie related data, including logs and command results!')) {
     //commands_statusbar.update_fail('Cancelled');
    return;
  }
     
  //commands_statusbar.update_sending('Removing zombie [id: ' + hb_id + '] ...');
  var url = "/api/hooks/" + escape(hb_id) + "/delete?token=" + token;
  Ext.Ajax.request({
    url: url,
    method: 'GET'
  });
```

Do make sure the delete for both online/offline will work the following code could be used.
Splits the id by `-` and references the last substring which contains the ID.

```Javascript
  var hb_id = this.contextNode.id.split('-')[2];
```
