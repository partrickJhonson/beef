Create a cross-domain SQLi scanner. The process will be similar to time delay sql injection detection.

The scanner will send a cross-domain HTTP request that will attempt to exploit a SQL injection vulnerability. The payload will delay the response from the server. Without breaking the same origin policy, the web browser can extrapolate the delay from the cross-domain server. 

Using the above technique repeatedly the scanner will test common locations on the application. 

This milestone includes stability and bug-fixing of the XssRays extension, that will be used as the delivery method and scanner of time-based blind SQLi payloads, and other tasks strictly related with the SQLi detection and exploitation mechanisms.

All the issues related to this milestone are outlined here:
[Cross domain time-based blind SQLi scanner](https://github.com/beefproject/beef/issues?sort=created&labels=Cross-domain+SQLi&direction=asc&state=open)

