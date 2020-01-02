## Summary
* **Objective**: This module removes the BeEF hook from the hooked page.
* **Date**: February 2012
* **Author**: bcoles
* **Browsers**: All
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/unhook)

## Internal Working

This modules does two actions:
* Look for script names hook.js and remove it
* delete BeEF objects and block current actions

**Warning**: This module will not work if the BeEF hook script has another name (changed in the BeEF configuration).

## Feedback