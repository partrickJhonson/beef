## Summary

* **Objective**: Find out network connection type of hooked phone
* **Authors**: mh
* **Browsers**: All (with phonegap)

* [Code](https://github.com/beefproject/beef/tree/master/modules/phonegap/phonegap_check_connection)

## Internal Working

use `navigator.network.connection.type` to determine connect type

```js
getConnectionType = function() {
    var states = {};
    states[Connection.UNKNOWN] = 'Unknown connection';
    states[Connection.ETHERNET] = 'Ethernet connection';
    states[Connection.WIFI] = 'WiFi connection';
    states[Connection.CELL_2G] = 'Cell 2G connection';
    states[Connection.CELL_3G] = 'Cell 3G connection';
    states[Connection.CELL_4G] = 'Cell 4G connection';
    states[Connection.NONE] = 'No network connection';
    return states[navigator.network.connection.type];
}
````

## Feedback

