## Summary

* **Objective**: Redirects the hooked page
* **Authors**: wade, vo
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/site_redirect)

## Internal Working

Note: **YOU WILL LOSE YOUR HOOK** (if the page you are redirecting to is not going to be hooked)

```js
window.location = "<%= @redirect_url %>";
```

## Feedback

