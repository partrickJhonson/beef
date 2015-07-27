## Introduction
The Autorun Rule Engine (ARE from now on) is a core BeEF component which allows you to define rules
that are automatically triggered on the hooked browser if certain conditions are matched.

If you are a BeEF aficionado, you were probably waiting for this form a long time. The old static autorun functionality has been removed. The main features of the new ARE are the following:
* **Dynamic** : pre-load rules from <beef_root>/arerules/enabled directory at start-up, or load them at runtime while BeEF is running, then trigger them on each hooked browser.
* **Non-intrusive** : command modules now have support for returning execution status and result data (useful for chaining). This didn't required a huge refactoring, but some smart changes in the API only.

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
* **Sequential** : call N modules with different configurable time delays.
Sequential mode wraps module bodies in their own function, using setTimeout() to trigger them with a time delay if specified. Execution order is also available to let you write down modules in an organised way in the JSON file, but then call them in different order. The resulting wrapper is something like this:
```javascript
 setTimeout(module_one(),   0);
 setTimeout(module_two(),   2000);
 setTimeout(module_three(), 3000);
```

Note that module execution status is not checked, and results are ignored. Useful if you just want to launch some modules without caring what their status will be (for instance, a bunch of blind XSRFs on a set of targets).

* **Nested-forward** : call N modules, where module N is executed only if N-1 returns a certain status. Module N can use as input the output from module N-1 (eventually mangling it before processing it).

## RESTful API
add/delete/list rule, trigger rule

## Rules examples:
various examples from public rules