## Summary

* **Objective**: Create an invisible iframe on the page
* **Authors**: passbe
* **Browsers**: All
* **Parameters**:
	* **URL**: the URL to load in the invisible iframe.

* [Code](https://github.com/beefproject/beef/tree/master/modules/misc/invisible_iframe)

## Internal Working


```js
        createInvisibleIframe: function() {
                var iframe = this.createElement('iframe', {
                                width: '1px',
                                height: '1px',
                                style: 'visibility:hidden;'
                        });

                document.body.appendChild(iframe);

                return iframe;
        },
```

## Feedback

