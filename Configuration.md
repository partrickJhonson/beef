# Configuring BeEF

BeEF should be configured through the main configuration file : [config.yaml](https://github.com/beefproject/beef/blob/master/config.yaml).

### Network limitations

Web interface for hooking or for managing BeEF can be limited by network subdomain. For example:

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
        public: "8.7.6.5" # Should be defined if BeEF is behind a NAT
        dns: "localhost" # Address of DNS server
        panel_path: "/ui/panel" # Path for UI panel
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

### Metasploit

The metasploit extension should be configured by modifying the [config.yml](https://github.com/beefproject/beef/blob/master/extensions/metasploit/config.yaml) fil in _extensions/metasploit_ :

```yaml
            name: 'Metasploit'
            enable: true
            host: "127.0.0.1"
            port: 55552
            user: "msf"
            pass: "abc123"
            uri: '/api'
            ssl: false
            ssl_version: 'SSLv3'
            ssl_verify: true
            callback_host: "127.0.0.1"
            autopwn_url: "autopwn"
```

Most of the configuration can be let with default value, except the **host** and **callback_host** parameters which should have the IP address of the host.

For enabling RPC communication, the following command should be launched in metasploit:

```ruby
load msgrpc ServerHost=127.0.0.1 Pass=abc123
```

This command can be written in a file and launched with **-r** option to _msfconsole_.

[[Images/msf1.png|align=center]]

Of course, IP address and password should be consistent with the previous yaml configuration file.

Once configured you can check that metasploit modules are loaded when launching BeEF:
![http://seckungfu.com/images/2012-6-27%2021-27-57.png](http://seckungfu.com/images/2012-6-27%2021-27-57.png)


***
[[Back|Installation]] | [[Next|Interface]]