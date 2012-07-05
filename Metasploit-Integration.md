###Start Metasploit###

Start Metasploit with `./msfconsole -r beef.rc`, where `beef.rc` is a file with the following contents:
`load msgrpc ServerHost=192.168.126.134 Pass=abc123`

![http://seckungfu.com/images/2012-6-27%2021-54-02.png](http://seckungfu.com/images/2012-6-27%2021-54-02.png)

###Configure BeEF###
Set the `host` and `callback_host` in `./beef/extensions/metasploit/config.yaml` to the same IP address used for `ServerHost`.
This is really important, otherwise if you use reverse shells the reverse connection will obviously fail.

Finally, enable the Metasploit extension in the main BeEF `config.yaml` file (in the root directory) and start BeEF with `./beef -x` or `ruby beef -x`. Note the 191 modules loaded from Metasploit.
![http://seckungfu.com/images/2012-6-27%2021-27-57.png](http://seckungfu.com/images/2012-6-27%2021-27-57.png)

Thanks to @lukesun629 for the images and some of the testing. He also wrote a chinese version of it here: http://seckungfu.com/blog/2012/06/29/how-to-use-metasploit-though-beef/