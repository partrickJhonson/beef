## Summary

* **Objective**: Return a string of the specified length
* **Authors**: wade
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/debug/test_return_long_string)

## Internal Working

just sends back all ascii chars within printable range

```js
var repeat_value = "<%= @repeat_string %>";
var iterations = <%= @repeat %>;
var str = "";

for (var i = 0; i < iterations; i++) {
    str += repeat_value;
}
beef.net.send("<%= @command_url %>", <%= @command_id %>, str, beef.are.status_success());
```

## Feedback

