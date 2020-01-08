## Summary

* **Objective**: Return the set of ascii chars
* **Authors**: wade
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/debug/test_return_ascii_chars)

## Internal Working

just sends back all ascii chars within printable range

```js

var str = '';
for (var i=32; i<=127;i++) str += String.fromCharCode(i);

beef.net.send("<%= @command_url %>", <%= @command_id %>, str, beef.are.status_success());

```

## Feedback

