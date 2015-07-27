## Introduction
The Autorun Rule Engine (ARE from now on) is a core BeEF component which allows you to define rules
that are automatically triggered on the hooked browser if certain conditions are matched.

If you are a BeEF aficionado, you were probably waiting for this form a long time. The old static autorun functionality has been removed.

ARE main features:
* **Dynamic** : pre-load rules from <beef_root>/arerules/enabled directory at start-up, or load them at runtime while BeEF is running, then trigger them on each hooked browser.
* **Non-intrusive** : command modules now have support for returning execution status and result data (useful for chaining). This didn't required a huge refactoring, but some smart changes in the API only.

## Matching
 browser/os

## Chaining mode
sequential or nested-forward

## RESTful API
add/delete/list rule, trigger rule

## Rules examples:
various examples from public rules
