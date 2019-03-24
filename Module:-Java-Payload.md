### Summary

Inject a malicious signed Java Applet (JavaPayload) that connects back to the attacker giving basic shell commands, command exec and wget.

Before launching it, be sure to have the JavaPayload StagerHandler listening, i.e.: `java javapayload.handler.stager.StagerHandler <payload> <IP> <port> -- JSh`

Note that modern Java (as of Java 7u51) will outright refuse to execute self-signed Java applets unless they're added to the exception list.

Refer to the [README](https://github.com/beefproject/beef/tree/master/modules/exploits/local_host/java_payload) for more information.