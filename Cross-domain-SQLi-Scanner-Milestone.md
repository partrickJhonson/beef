Create a cross-domain SQLi scanner. The process will be similar to time delay sql injection detection.

The scanner will send a cross-domain HTTP requests that will attempt to exploit a SQL injection vulnerability. The payload will delay the response from the server. Without breaking the same origin policy the web browser can extrapolate the delay from the cross-domain server. 

Using the above technique repeatedly the scanner will test common locations on the application. 
