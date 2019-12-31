## Summary
* **Objective**: This module will retrieve the HTML from the current page.
* **Date**: ???
* **Authors**: bcoles
* **Browsers**: All
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_page_html]]

## Internal Working

This module returns the HTML of the header and body of the hooked web page :

```javascript
try {
	var html_head = document.head.innerHTML.toString();
} catch (e) {
	var html_head = "Error: document has no head";
}
try {
	var html_body = document.body.innerHTML.toString();
} catch (e) {
	var html_body = "Error: document has no body";
}
```

## Feedback