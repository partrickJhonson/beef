## Summary

* **Objective**: rewrite a selected real URL link to a fake url
* **Authors**: bcoles, xntrik, majorsecurity.net
* **Browsers**: Safari <= 5.1
* **Parameters**:
	* **Fake URL**
	* **Real URL**
	* **jQuery selector**: selector for the element of the page in jQuery notation.

* [Code](https://github.com/beefproject/beef/tree/master/modules/hooked_domain/mobilesafari_address_spoofing)

## Internal Working

Spoofs the selected link element by setting a callback via jquery when that link is clicked on.

```js

$j('<%= @domselectah %>').each(function() {
        $j(this).attr('href','#').click(function() {
                somethingsomething();
                return true;
        });
});

```

## Feedback
