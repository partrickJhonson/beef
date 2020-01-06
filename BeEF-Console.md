_**The console extension is currently **disabled** and **unsupported**, this page is kept for historical purposes only in the case that this is enabled again.**_

## Introduction

BeEF includes a metasploit-like console. This console can be used to control hooked browsers and send modules.

## Configuration

The BeEF console is an extension which should be enabled in the main _config.yml_ file.

## Utilization

The console is automatically launched with the beef script.

### Help

```
Core Commands
=============

    Command       Description
    -------       -----------
    ?             Help menu
    back          Move back from the current context
    exit          Exit the console
    help          Help menu
    irb           Drops into an interactive Ruby environment
    jobs          Print jobs
    offline       List previously hooked browsers
    online        List online hooked browsers
    quit          Exit the console
    review        Target a particular previously hooked (offline) hooked browser
    show          Displays 'zombies' or 'browsers' or 'commands'. (For those who prefer the MSF way)
    target        Target a particular online hooked browser
```

### Hooked browsers

```
BeEF > online

Currently hooked browsers within BeEF

Id  IP        Browser  OS
--  --        -------  --
6   10.1.1.1  C-21     Linux

BeEF > offline

Previously hooked browsers within BeEF

Id  IP        Browser  OS
--  --        -------  --
1   10.1.1.2  FF-15    Windows XP
[...]
```

### Jobs

```
BeEF > jobs -l

Id  Job Name
--  --------
0   http_hook_server
```

### Launch module

**Select the target zombie**:
```
BeEF > target 6
```

**List available modules** :
```
BeEF (10.1.1.1) [6] > commands

List command modules for this target
Id   Command                                               Status       Execute Count
--   -------                                               ------       -------------
1    Host/Hook_Default_Browser                             User Notify  0
2    Host/Detect_CUPS                                      Working      0
3    Host/Get_Clipboard                                    Not Working  0
4    Host/Get_Registry_Keys                                Not Working  0
5    Host/Get_Wireless_Keys                                User Notify  0
[...]
```

**Select a module**:
```
BeEF (10.1.1.1) [6] > select 66
```

**See information on the module**:
```
BeEF (10.1.1.1) [6] / Detect Google Desktop > cmdinfo
Module name: Detect Google Desktop
Module category: Host/
Module description: This module attempts to detect Google Desktop running on the default port 4664.
```

**Launch the module**:
```
BeEF (10.1.1.1) [6] / Detect Google Desktop > execute
[*] Command successfully queued
[13:21:24][*] Hooked browser [id:6, ip:10.1.1.1] has been sent instructions from command module 'Detect Google Desktop'
```

**See response**:
```
BeEF (10.1.1.1) [6] / Detect Google Desktop > response

List of responses for this command module:
Id  Executed Time     Response Time
--  -------------     -------------
48  2012-10-15 13:18  2012-10-15 13:19:04 +0200
51  2012-10-15 13:21  2012-10-15 13:21:29 +0200

BeEF (10.1.1.1) [6] / Detect Google Desktop > response 51
Results retrieved: 2012-10-15 13:21:29 +0200

Response:
google_desktop=Not Installed
```
***
[[Notifications|Notifications]] | [[Module creation|Module creation]]