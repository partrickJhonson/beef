# Configuring BeEF

BeEF should be configured through the main configuration file : [config.yaml](https://github.com/beefproject/beef/blob/master/config.yaml).

***

## Authentication

### Credentials

**Be sure to change the username and password for the web interface.**

For example:

```yaml
    credentials:
        user:   "beef"
        passwd: "beef"
```

### Network limitations

The web interface for hooking or for managing BeEF can be limited by subnet.

**Access to the management interface should be restricted using the `permitted_ui_subnet` access control.**

For example:

```yaml
    restrictions:
        permitted_hooking_subnet: "10.1.0.0/16"
        permitted_ui_subnet: "127.0.0.1/32"
```

The panel path should also be changed using the `beef.http.web_ui_basepath` configuration option (see Web server configuration section below). Note: this is security through obscurity and won't prevent attacks against the `/api/` REST interface.


### Login Throttling

By default, the administration UI throttles login attempts to 1 attempt per second. This can be changed using the `beef.extensions.admin_ui.login_fail_delay: 1` value in `extensions/admin_ui/config.yaml`.

Note: This does not prevent login brute-force attacks against the `/api/` REST API interface which does not have the same restrictions.


***

## Web server configuration

The web server can be fully configured :

```yaml
    http:
        debug: false # Will print verbose message in BeEF console
        host: "0.0.0.0" # IP address of the web server
        port: "3000" #Port of the web server

        # If BeEF is running behind a reverse proxy or NAT
        #  set the public hostname and port here
        public: "8.7.6.5"
        public_port: "3000"

        dns: "localhost" # Address of DNS server
        web_ui_basepath: "/ui" # Path for admin UI
        hook_file: "/hook.js" # Path for hooking script
        hook_session_name: "BEEFHOOK" #Name of session
        session_cookie_name: "BEEFSESSION" # Name of BeEF cookie
```

### Web server imitation

BeEF also features rudimentary web server imitation. The root page and HTTP 404 error pages can be changed to reflect one of several popular web servers (apache, iis, nginx) using the `beef.http.web_server_imitation` directive.

For example:

```yaml
        # Imitate a specified web server (default root page, 404 default error page, 'Server' HTTP response header)
        web_server_imitation:
            enable: true
            type: "apache" # Supported: apache, iis, nginx
            hook_404: false # inject BeEF hook in HTTP 404 responses
            hook_root: false # inject BeEF hook in the server home page
```

The `hook_404` and `hook_root` directives can be enabled to inject the BeEF hook on HTTP 404 error pages and the web root page respectively. This will hook the browser of anyone examining the web server.


***

## Configuring Extensions

### Enabling extensions

Extensions should be enabled in the main [config.yaml](https://github.com/beefproject/beef/blob/master/config.yaml):

```yaml
    extension:
        requester:
            enable: true
        proxy:
            enable: true
        metasploit:
            enable: false
        social_engineering:
            enable: true
        evasion:
            enable: false
        console:
             shell:
                enable: false
```

The Demos extension should be disabled in production by setting `enable: false` in [extensions/demos/config.yaml](https://github.com/beefproject/beef/blob/master/extensions/demos/config.yaml)

### Metasploit

The Metasploit extension should be configured by modifying the [config.yml](https://github.com/beefproject/beef/blob/master/extensions/metasploit/config.yaml) file in _extensions/metasploit_ :

```yaml
            name: 'Metasploit'
            enable: true
            host: "127.0.0.1"
            port: 55552
            user: "msf"
            pass: "<password>"
            uri: '/api'
            ssl: true
            ssl_version: 'TLS1'
            ssl_verify: true
            callback_host: "127.0.0.1"
            autopwn_url: "autopwn"
```

**Be sure to change the `password` field**. Authenticated access to the Metasploit RPC service can be used to [execute arbitrary commands](https://www.rapid7.com/db/modules/exploit/multi/misc/msf_rpc_console) on the underlying operating system.

Most of the configuration can be let with default value, except the **host** and **callback_host** parameters which should have the IP address of the host.

For enabling RPC communication, the following command should be launched in Metasploit:

```ruby
load msgrpc ServerHost=127.0.0.1 User=msf Pass=<password> SSL=y
```

This command can be written in a file and launched with **-r** option to _msfconsole_.

[[Images/msf1.png|align=center]]

Of course, IP address and password should be consistent with the previous yaml configuration file.

### Launching BeEF

You can now launch BeEF by launching the beef script in the root directory :

[[Images/conf-launch.png|align=center]]

You can also use the following options :
```
Usage: beef [options]
    -x, --reset                      Reset the database
    -v, --verbose                    Display debug information
    -a, --ascii_art                  Prints BeEF ascii art
    -c, --config FILE                Load a different configuration file: if it's called custom-config.yaml, git automatically ignores it.
    -p, --port PORT                  Change the default BeEF listening port
    -w, --wsport WS_PORT             Change the default BeEF WebSocket listening port
```

Once configured you can check that metasploit modules are loaded when launching BeEF:

[[Images/conf_metasploit.png|align=center]]


***
[[Back|Installation]] | [[Next|Interface]]
