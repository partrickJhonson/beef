### What is the default login for BeEF?

BeEF is configured with default placeholder credentials of `beef` / `beef`.

However, BeEF will not start if configured with these credentials. The credentials must be changed in the configuration file `config.yaml`.


### How do I configure integration with Metasploit?

Be sure to read the [[documentation|Metasploit]] (and [[here|Configuration]] also), and take care especially of the following points :

* Enable MSF integration by changing `beef.extension.metasploit.enable` to true in BeEF's main config.yaml file.
* Ensure you load the msgrpc interface in Metasploit before starting BeEF: `msf > load msgrpc ServerHost=127.0.0.1 Pass=abc123 SSL=y`
* Ensure that the IP address supplied to Metasploit with the `ServerHost` parameter is the same IP address as specified in `beef.extension.metasploit.host`
* Ensure that the IP address specified in `beef.extension.metasploit.callback_host` is the publicly accessible IP address for victim connections to Metasploit.
* Ensure that if `SSL=y` was supplied to Metasploit when starting msgrpc then `beef.extension.metasploit.ssl` is set to `true`.


### How do I configure BeEF on a server behind NAT?

[Forward](https://en.wikipedia.org/wiki/Port_forwarding) the public port (default 3000/tcp) from your border router to `<LAN IP>:3000` of the BeEF server.

Check that your network configuration is working correctly by attempting to access the admin panel:

```
http://<your WAN IP address>:3000/ui/panel
```

If you cannot access the admin panel, then your network configuration is broken. BeEF does not have access to your router and cannot configure your network for you. You'll need to review your network configuration to ensure the port is forwarded correctly.

Once you've confirmed that port 3000 is accessible remotely, ensure `beef.http.public` and `beef.http.public_port` are set to the public WAN IP address and public WAN port respectively in `config.yaml`. Note, you'll need to restart BeEF after making changes to the configuration file.

Additionally, ports `61985/tcp` and `61986/tcp` must also be forwarded if web sockets are enabled for communicating with BeEF. Likewise, some BeEF extensions, such as IPEC and DNS, require additional ports to be forwarded. Review the associated `config.yaml` file for each extension and ensure the appropriate ports are forwarded.


### How do I configure BeEF with ngrok?

[Download ngrok](https://ngrok.com/), then tunnel your BeEF port (default: `3000`):

This can be achieved with the following command, which tells ngrok to open a tunnel from port `80` on the public server to port `3000` on your local host.

```
$ ngrok http 3000
```

Specify the public domain name `beef.http.public` and public port `beef.http.public_port` in `config.yaml`:

```yaml
        public: "<your-id>.ngrok.io"      # public hostname/IP address
        public_port: "80"                 # public port (experimental) 
```

You should then be able to access BeEF using the following URL:

```
http://<your-id>.ngrok.io/ui/panel
```

### Can I use a domain name instead of IP address for the BeEF hook?

Yes! Simply specify the public domain name and port in `beef.http.public` and `beef.http.public_port` respectively in `config.yaml`.


### How do I fix `ArgumentError - invalid byte sequence in US-ASCII` ?

Set the appropriate locale:

```bash
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```

### Why does BeeF update fail?

If you're getting the error `Your local changes to the following files would be overwritten by merge: Gemfile.lock` it means BeEF's dependencies were recently updated.

To fix, run `git checkout Gemfile.lock`, then update BeEF and run `bundle install` to install the updated packages.
