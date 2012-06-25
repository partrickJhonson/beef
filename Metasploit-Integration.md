###Start Metasploit###

Start Metasploit with `./msfconsole -r beef.rc`, where `beef.rc` is a file with the following contents:
`load msgrpc ServerHost=172.16.67.1 Pass=abc123`

###Configure BeEF###
Set the `host` and `callback_host` in `./beef/extensions/metasploit/config.yaml` to the same IP address used for `ServerHost`.

Finally, enable the Metasploit extension in the main BeEF `./config.yaml` and start BeEF `./beef`.
