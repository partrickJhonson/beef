## Summary

* **Objective**: Perform a ping sweep of the network
* **Authors**: jgaliana
* **Browsers**: Firefox (< 60)

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/ping_sweep_ff)

## Internal Working

It works by calling a Java method from JavaScript and does not require user interaction. It doesn't always work on Firefox.

```js

function do_scan(host, timeout) {
        var status=false;
        var ping="";

        try {
                status = java.net.InetAddress.getByName(host).isReachable(timeout);
        } catch (e) { /*handle exception...? */ }

        if (status) {
                ping = host + " is alive!";
        } else if (verbose) {
                ping = host + " is not alive";
        }
        return ping;
}


```

## Screenshots

[[Images/module-ping-sweep1.png|align=center]]

[[Images/module-ping-sweep2.png|align=center]]

## Feedback

* The default value (2000 ms) seems to be valid for virtual network
* Users should take care of the IP range format : **10.1.1.1-10.1.1.3** is valid, **10.1.1.1-3** is not