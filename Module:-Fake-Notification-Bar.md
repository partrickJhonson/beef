## Summary

* **Objective**: Get user to download and run malicious file through a notification
* **Authors**: xntrik
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/fake_notfication)

## Internal Working

Displays a fake notification bar at the top of the screen, similar to those presented in IE.

The file will need to be hosted on the path specified on the file system.

```js
var el = beef.dom.createElement('div',{'id':id,'style':'width:100%; position:fixed; top:0px; left:0px; margin:0; padding:2px 20px 5px 24px; z-index:'+zztop+'; border-bottom:1px solid black; background:#ffffda; display:none; font-family: \'Tahoma\',sans-serif; font-size: 12px; '});
```


## Feedback

