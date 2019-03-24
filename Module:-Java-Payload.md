### Summary

Inject a malicious signed Java Applet (JavaPayload) that connects back to the attacker giving basic shell commands, command exec and wget.

Before launching it, be sure to have the JavaPayload StagerHandler listening, i.e.: `java javapayload.handler.stager.StagerHandler <payload> <IP> <port> -- JSh`

Note: This won't work with modern browsers and modern Java.

Refer to the [README](https://github.com/beefproject/beef/tree/master/modules/exploits/local_host/java_payload) for more information.