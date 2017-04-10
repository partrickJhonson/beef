# Configuring BeEF

BeEF should be configured through the main configuration file : [config.yaml](https://github.com/beefproject/beef/blob/master/config.yaml).


### Credentials

Be sure to change the username and password for the web interface. For example:

```yaml
    credentials:
        user:   "beef"
        passwd: "beef"
```

### Network limitations

The web interface for hooking or for managing BeEF can be limited by subnet. For example:

```yaml
    restrictions:
        permitted_hooking_subnet: "10.1.0.0/16"
        permitted_ui_subnet: "127.0.0.1/32"
```

### Web server configuration

The webserver can be fully configured :

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
            pass: "abc123"
            uri: '/api'
            ssl: true
            ssl_version: 'TLS1'
            ssl_verify: true
            callback_host: "127.0.0.1"
            autopwn_url: "autopwn"
```

Most of the configuration can be let with default value, except the **host** and **callback_host** parameters which should have the IP address of the host.

For enabling RPC communication, the following command should be launched in Metasploit:

```ruby
load msgrpc ServerHost=127.0.0.1 User=msf Pass=abc123 SSL=y
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
