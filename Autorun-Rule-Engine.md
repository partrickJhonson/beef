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
sequential or nested-forward

## RESTful API
add/delete/list rule, trigger rule

## Rules examples:
various examples from public rules