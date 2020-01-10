## Summary

* **Objective**: Detect if the target is in TOR network
* **Authors**: wade, pdp, bm, xntrik
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/detect_tor)

## Internal Working

attempts to load an image from the Tor network and check if it loads.

The default URL to load is 

http://xycpusearchon2mc.onion/deeplogo.jpg


```js
img.src = '<%= @tor_resource %>';
img.id = 'torimg';
img.setAttribute("attr","start");
img.onerror = function() {
        this.setAttribute("attr","error");
};
img.onload = function() {
        this.setAttribute("attr","load");
};

````

## Feedback

