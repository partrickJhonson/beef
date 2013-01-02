##Summary
* **Objective**: Sends an alert dialog to the hooked browser.
* **Date**: ???
* **Authors**: wade, bm
* **Browsers**: All
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/alert_dialog]]

##Internal Working

Really basic, here is the whole code :
```javascript
beef.execute(function() {
alert("<%== format_multiline(@text) %>");

beef.net.send("<%= @command_url %>", <%= @command_id %>, "text=<%== format_multiline(@text) %>");
});
```

## Screenshots

[[Images/module-alert-dialog1.png|align=center]]

[[Images/module-alert-dialog2.png|align=center]]

##Feedback

* So basic, that it should work on any browser any version.

