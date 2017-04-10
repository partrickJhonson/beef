## Summary

* **Objective** : This module will retrieve the physical location of the hooked browser using the Geo-location API. The user will be prompted to share their location with the hooked origin, unless the hooked origin has been white-listed previously.
* **Authors**: antisnatchor
* **Browsers**:
  * Internet Explorer 9 to latest
  * Firefox 3.5 to latest
  * Opera 10.6 to latest
  * Chrome 5 to latest
  * Safari 5 to latest
* [Code](https://github.com/beefproject/beef/tree/master/modules/host/physical_location)

## Internal Working

This module uses the [`beef.geolocation.getGeolocation`](https://github.com/beefproject/beef/blob/master/core/main/client/geolocation.js) function in the BeEF core.
