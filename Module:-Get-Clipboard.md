_TODO_## Summary

* **Objective**: Steals content of the user's clipboard
* **Authors**: bcoles
* **Browsers**: IE 6-8 (IE 7&8 will prompt for permission)

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/clipboard_theft)

## Internal Working

Uses the `clipboardData` API to retrieve content, and send it back in plaintext via a GET request.

```js
var clipboard = clipboardData.getData("Text");
```

## Feedback

