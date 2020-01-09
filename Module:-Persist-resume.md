## Summary

* **Objective**: Persist over applications sleep/wake events
* **Authors**: mh
* **Browsers**: All (Requires PhoneGap API)

* [Code](https://github.com/beefproject/beef/tree/master/modules/phonegap/phonegap_persist_resume)

## Internal Working

adds an event listener for persistence upon the "resume" event

```js
document.addEventListener("resume", beef_init(), false);
result = 'success';
```

## Feedback

