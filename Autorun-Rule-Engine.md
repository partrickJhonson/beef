## Introduction
The Autorun Rule Engine (ARE from now on) is a core BeEF component which allows you to define rules
that are automatically triggered on the hooked browser if certain conditions are matched.

If you are a BeEF aficionado, you were probably waiting for this form a long time. The old static autorun functionality has been removed. The main features of the new ARE are the following:
* **Dynamic** : pre-load rules from <beef_root>/arerules/enabled directory at start-up, or load them at runtime while BeEF is running, then trigger them on each hooked browser. RESTful API calls are documented in detail later here.
* **Non-intrusive** : command modules now have support for returning execution status and result data (useful for chaining). This didn't required a huge refactoring, but some smart changes in the API only. If you need chain modules output/input though, you will need to add one or two lines of dumb-proof JavaScript to the command modules if the rule is in nested-forward chain mode (more on this later here).

## Matching
On successful hook, the ARE checks if any rulesets present in the core_arerules table match against the hooked browsers. Various hooked browser properties are checked:
* Browser type and version
* Operating system type and version
* (WIP) Plugin type/version
* (WIP) OS architecture

Trigger only on Safari browsers >= 7, on OSX Yosemite or below.
```javascript
{
  "browser": "S",
  "browser_version": ">= 7",
  "os": "OSX",
  "os_version": "<= 10.10"
}
```

Trigger only on Internet Explorer (any version), on Windows 7 or greater.
```javascript
{
  "browser": "IE",
  "browser_version": "ALL",
  "os": "Windows",
  "os_version": ">= 7"
}
```

Trigger only on Firefox (at least version 31), on any Linux system.
```javascript
{
  "browser": "FF",
  "browser_version": ">= 31",
  "os": "Linux",
  "os_version": "ALL"
}
```

The following are the allowed Browser/OS types and version supported with the ARE:
```ruby
  BROWSER = ['FF','C','IE','S','O','ALL']
  OS = ['Linux','Windows','OSX','Android','iOS','BlackBerry','ALL']
  VERSION = ['<','<=','==','>=','>','ALL','Vista','XP']
```
Have a look in browser.js and os.js (<beef_root>/core/main/client) to see exactly what is supported.

## Chaining mode
There are currently two chain modes implemented, which should cover most of your client-side needs.
### Sequential
Call N modules with different configurable time delays.
Sequential mode wraps module bodies in their own function, using setTimeout() to trigger them with a time delay if specified. Execution order is also available to let you write down modules in an organised way in the JSON file, but then call them in different order. 

Note that module execution status is not checked, and results are ignored. Useful if you just want to launch some modules without caring what their status will be (for instance, a bunch of blind XSRFs on a set of targets).

The resulting wrapper is something like this:
```javascript
 setTimeout(module_one(),   0);
 setTimeout(module_two(),   2000);
 setTimeout(module_three(), 3000);
```

### Nested-forward
Call N modules, where module N is executed only if N-1 returns a certain status. Module N can use as input the output from module N-1 (eventually mangling it before processing it).

Nested-forward mode wraps module bodies in their own function, then start to execute them from the first, polling for command execution status/results (with configurable polling interval and timeout). After execution of the first module in the chain, depending on the module condition specified, execution will continue or stop.

The following is an example of chaining an internal network fingerprinting activity only if the hooked browser internal IP is known. Two modules are chained: get_internal_ip_webrtc and internal_network_fingerprinting.

```javascript
{
"modules": [
    {"name": "get_internal_ip_webrtc",
      "condition": null,
      "code": null,
      "options": {}
    },
    {"name": "internal_network_fingerprinting",
      "condition": "status==1",
      "code": "var s=get_internal_ip_webrtc_mod_output.split('.');var start=parseInt(s[3])-1;var end=parseInt(s[3])+1;var mod_input = s[0]+'.'+s[1]+'.'+s[2]+'.'+start+'-'+s[0]+'.'+s[1]+'.'+s[2]+'.'+end;",
      "options": {
        "ipRange":"<<mod_input>>",
        "ports":"80",
        "threads":"5",
        "wait":"2",
        "timeout":"10"
      }
    }
  ],
  "execution_order": [0,1],
  "execution_delay": [0, 0],
  "chain_mode": "nested-forward"
}
```

The wrapper created for this rule will be something like:

module_one()
if module_one_result == success
     module_two(module_one_output) // IP retrieved with first module

This is also one of the cases where the second module input expects something different than the first module output, so we need a way to change module output. The code property allows you to specify arbitrary JavaScript (no multilines, one line only). In this specific case, let's assume the output of the first module is 172.16.35.166. The  
second module requires an input like the following though: "start_ip-stop_ip", as in 172.16.35.160-172.16.35.170 for internal network fingerprinting. The following is the code property value for the second module:
```javascript
var s = get_internal_ip_webrtc_mod_output.split('.');
var start = parseInt(s[3])-1;
var end = parseInt(s[3])+1;
var mod_input = s[0]+'.'+s[1]+'.'+s[2]+'.'+start+'-'+s[0]+'.'+s[1]+'.'+s[2]+'.'+end;
```
As you can see it's dumb-proof. 

Note: command result status is checked, and you can properly chain input into output, having also
the flexibility of slightly mangling it to adapt to module needs.
Note: Useful in situations where you want to launch 2 modules, where the second one will execute only
if the first once return with success. Also, the second module has the possibility of mangling first
module output and use it as input for some of its module inputs.

## RESTful API
add/delete/list rule, trigger rule

## Rules examples:
various examples from public rules