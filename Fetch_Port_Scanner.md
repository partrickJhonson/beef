## Summary

* **Description**: Uses fetch to test the response in order to determine if a port is open or not."
* **Authors**: Crimes by will, jcrew99
* **Browsers**: Firefox, Chrome
* **Parameters** :
   * **ipHost** : IP or hostname of the target to be scanned (only one per command)
   * **ports** : list of ports to be scanned

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/fetch_port_scanner)

## Internal Working
There are two defined types of ports that are in an array which can be used for common ports.
They are these, which you can use type in for ports which contain a common list to be scanned:
 * default 
 * top

There is a list of blocked ports which will not be scanned which are ones that will not return 

The scan has a timeout timer of 5 seconds for a response, based on testing this was what got the most common response times. 
It does a lot of checks in the command module for the type of browser and response times, see below in the code for what the times are.
They can be found here:
* [Code](https://github.com/beefproject/beef/tree/master/modules/network/fetch_port_scanner/command.js)

There are a statements to check what the type of browser is and uses that to determine what type it is and then uses those responses to determine if a port is open.

The times have been determined after testing but may be subject to environment issues, please let us know if there are any issues. 
A common issue is that if a port isnt returning back data it can lead to timeout.

If a port is not sending back information it is possible that its in use by something else, its unfortunately hard to tell if thats the case as firefox and chrome may not send back any information. 


## Feedback