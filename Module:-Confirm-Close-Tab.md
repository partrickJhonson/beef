## Summary
* **Objective**: Shows a confirm dialog to the user when he tries to close a tab. If he click yes, re-display the confirm dialog. Doesn't work on Opera
* **Authors**: antisnatchor
* **Browsers**: All except Opera (User is always notified)
* **Parameters** : No parameters given
* [Code](https://github.com/beefproject/beef/tree/master/modules/persistence/confirm_close_tab)

##Internal Working

This modules uses the confirm function to prompt the user and the automated window.onbeforeunload to ask it several times :

```javascript
    function display_confirm(){
        if(confirm("Are you sure you want to navigate away from this page?\n\n There is currently a request to the server pending. You will lose recent changes by navigating away.\n\n Press OK to continue, or Cancel to stay on the current page.")){
            display_confirm();
        }
    }

    function dontleave(e){
        e = e || window.event;

        if(beef.browser.isIE()){
            e.cancelBubble = true;
            e.returnValue = "There is currently a request to the server pending. You will lose recent changes by navigating away.";
        }else{
            if (e.stopPropagation) {
                e.stopPropagation();
                e.preventDefault();
            }
        }

        //re-display the confirm dialog if the user clicks OK (to leave the page)
        display_confirm();
        return "There is currently a request to the server pending. You will lose recent changes by navigating away.";
    }

    window.onbeforeunload = dontleave;
```

## Screenshots

_Error message on Chrome_ :
[[Images/module-confirm-close-tab1.png|align=center]]

_Second error message on Chrome_ :
[[Images/module-confirm-close-tab2.png|align=center]]

## Feedbacks

* Not very stealth but it works very well
* Not very reliable on Chrome, only the first message is prompted sometimes