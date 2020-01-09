## Summary

* **Objective**: Discover DNS hostnames within the victim's network
* **Authors**: jgaliana
* **Browsers**: Firefox, Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/dns_enumeration)

## Internal Working

```js

    function do_resolv(url) {
        // Cross Origin Resource Sharing call
        var xhr = new XMLHttpRequest();
        if("withCredentials" in xhr) {
            xhr.open("GET", url, true);
        } else if(typeof XDomainRequest != "undefined") {
            xhr = new XDomainRequest();
            xhr.open("GET",url);
        } else {
            return -1;
        }

        xhr.onreadystatechange= function(e) { if(xhr.readyState==4) { clearTimeout(p); check_next(); } };
        xhr.send();
        var p = setTimeout(function() { xhr.onreadystatechange = function(evt) {}; notify(); }, timeout);
    }

```


## Screenshots

[[Images/module-dns-enumeration1.png|align=center]]

## Feedback


