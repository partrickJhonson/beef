## Summary

* **Objective**: Executes Raw Javascript in the browser
* **Authors**: wade, vo
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/misc/raw_javascript)

## Internal Working

This module will send the code entered in the 'JavaScript Code' section to the selected hooked browsers where it will be executed. Code is run inside an anonymous function and the return value is passed to the framework. Multiline scripts are allowed, no special encoding is required.


```js
var result;

try {
        result = function() {<%= @cmd %>}();
} catch(e) {
        for(var n in e)
                result+= n + " " + e[n] + "\n";
}
```


## Feedback

