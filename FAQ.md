### What is the default login for BeEF?
By default, beef/beef is the login. Check out the [[ documentation | https://github.com/beefproject/beef/wiki/Interface]].


### How do I configure integration with Metasploit?

Be sure to read the [[documentation|Metasploit]] (and [[here|Configuration]] also), and take care especially of the following points :

* Enable MSF integration by changing `beef.extension.metasploit.enable` to true in BeEF's main config.yaml file.
* Ensure you load the msgrpc interface in Metasploit before starting BeEF: `msf > load msgrpc ServerHost=127.0.0.1 Pass=abc123 SSL=y`
* Ensure that the IP address supplied to Metasploit with the `ServerHost` parameter is the same IP address as specified in `beef.extension.metasploit.host`
* Ensure that the IP address specified in `beef.extension.metasploit.callback_host` is the publicly accessible IP address for victim connections to Metasploit.
* Ensure that if `SSL=y` was supplied to Metasploit when starting msgrpc then `beef.extension.metasploit.ssl` is set to `true`.


### How do I configure BeEF on a server behind NAT?
* Ensure `beef.http.public` and `beef.http.public_port` are set to the public WAN IP address and public WAN port respectively.
* Forward the public port (default 3000/tcp) from your border router to `<LAN IP>:3000` of the BeEF server.
* Additionally, ports 61985/tcp and 61986/tcp must also be forwarded if web sockets are enabled for communicating with BeEF.
* Likewise, some BeEF extensions, such as IPEC and DNS, require additional ports to be forwarded. Review the associated config.yaml file for each extension and ensure the appropriate ports are forwarded.


### Can I use a domain name instead of IP address for the BeEF hook?

Yes! Simply specify the public domain name and port in `beef.http.public` and `beef.http.public_port` respectively.


### Why does BeeF update fail?

If you're getting the error `Your local changes to the following files would be overwritten by merge: Gemfile.lock` it means BeEF's dependencies were recently updated.

To fix, run `git checkout Gemfile.lock`, then update BeEF and run `bundle install` to install the updated packages.
