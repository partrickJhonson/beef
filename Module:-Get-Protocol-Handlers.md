## Summary

* **Objective**: Identify protocol handlers supported in a browser
* **Authors**: bcoles
* **Browsers**: Firefox, IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/detect_protocol_handlers)

## Internal Working

This module launches invisible iframes in order to attempt to load a resource with different protocols schemes. It then detects if the resource loads or not to determine availability of a protocol handler.

Firefox users are prompted to launch the application for which the protocol handler is responsible (if applicable).

Firefox users are also warned when there is no application assigned to a protocol handler (In the js console of the browser).

The possible return values are: 
* unknown
* exists
* does not exist.

```js

//implementation for firefox

var protocol_iframe = document.createElement('iframe');
protocol_iframe.setAttribute('id', "protocol_iframe_<%= @command_id %>");
protocol_iframe.setAttribute('src', "");
protocol_iframe.setAttribute('style', "display:none;height:1px;width:1px;border:none");
document.body.appendChild(protocol_iframe);

for (var i=0; i<handler_protocol.length; i++) {
        var result = "";
        var protocol = handler_protocol[i];
        try {
                document.getElementById('protocol_iframe_<%= @command_id %>').contentWindow.location = protocol+"://"+handler_addr;
        } catch(e) {
                if (e.name == "NS_ERROR_UNKNOWN_PROTOCOL")
                     result = protocol + " does not exist";
                else result = protocol + " unknown";
        }
        if (!result) result = protocol + " exists";
        handler_results.push(result);
}

```


## Feedback

