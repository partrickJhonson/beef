## Summary

* **Description**: Scan ports in a given hostname, using WebSockets, CORS and img tags. It uses the three methods to avoid blocked ports or Same Origin Policy."
* **Authors**: Crimes by will, jcrew99
* **Browsers**: Firefox, Chrome
* **Parameters** :
   * **IP or Hostname** : IP or hostname of the target to be scanned (only one per command)
   * **Specific ports to scan** : list of ports to be scanned
   * **Closed port timeout** : Time-out to detect closed port (in ms, default is 1100)
   * **Open port time-out** : Time-out to detect open port (in ms, default is 2500ms)
   * **Delay between requests** : in ms, default is 600ms
   * **Debug** : Debug mode set to false by default
* [Code](https://github.com/beefproject/beef/tree/master/modules/network/port_scanner)

## Internal Working

[Description to be done] Code is [here](https://github.com/beefproject/beef/blob/master/modules/network/port_scanner/command.js)

## Screenshots

_Command_ :
[[Images/module-port-scanner1.png|align=center]]

_Result_ :
[[Images/module-port-scanner2.png|align=center]]

## Feedback