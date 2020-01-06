## Summary
* **Objective**: Detect if popup blocker is enabled.
* **Date**:
* **Author**: wade
* **Browser**: All (user notify)
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/detect_popup_blocker)

## Internal Working

Uses the **beef.browser.popup.blocker_enbabled** function ([here](https://github.com/beefproject/beef/blob/master/core/main/client/browser/popup.js)):

```javascript
    blocker_enbabled: function () {
        screenParams = beef.browser.getScreenSize();
        var popUp = window.open('/', 'windowName0', 'width=1, height=1, left='+screenParams.width+',     top='+screenParams.height+', scrollbars, resizable');
        if (popUp == null || typeof(popUp)=='undefined') {
            return true;
        } else {
            popUp.close();
            return false;
        }
    }
```

## Feedback

* **IE6** seems to block popup
* **Firefox 15** seems to allow popup (without extension)

