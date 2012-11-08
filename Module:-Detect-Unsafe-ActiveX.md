## Summary

* **Objective** : This module will check if IE has been insecurely configured. It will test if the option _Initialize and script ActiveX controls not marked as safe for scripting_ is enabled.The setting can be found in: _Tools Menu -> Internet Options -> Security -> Custom level -> "Initialize and script ActiveX controls not marked as safe for scripting"_
* **Date**: January 2012
* **Authors**: Wade, bcoles
* **Browser**: IE
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/detect_unsafe_activex)

## Internal Working

This module try to load the ActiveX object _WbemScripting.SWbemLocator_ :
```javascript
    try {
        test = new ActiveXObject("WbemScripting.SWbemLocator");
    } catch (e) {
        unsafe = false;
    }
    if (unsafe) {
        result = "Browser is configured for unsafe ActiveX";
    } else {
        result = "Browser is NOT configured for unsafe ActiveX";
    }
```

## Feedback

* **IE6**: Unsafe by default (tested on IE6.0.2900.5512 on Win XPSP3)

## References
