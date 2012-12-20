##Summary
* **Objective**: Fingerprint browser version by checking presence of browser images
* **Date**: Septembre 2011
* **Authors**: bcoles
* **Browsers**: IE, Safari, Firefox
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/browser_fingerprinting]]

##Internal Working

The module include a database of pictures accessible internally by the browser :

```javascript
var fingerprints = new Array(
    new Array("Safari","1+","feed://__rsrc__/__rsrc__/NextPage.tif"),
    new Array("Firefox","1+","moz-icon://.autoreg?size=16"),
    new Array("Firefox","2","resource:///res/html/gopher-audio.gif"),
    new Array("Firefox","2-3","jar:resource:///chrome/classic.jar!/skin/classic/browser/Secure.png"),
    new Array("Firefox","4-5","resource:///chrome/browser/skin/classic/browser/Secure.png"),
    new Array("Firefox","1-6","resource:///chrome/browser/content/branding/icon128.png"),
    new Array("Firefox","4+","resource:///chrome/browser/skin/classic/browser/Geolocation-16.png"),
    new Array("Firefox","7+","resource:///chrome/browser/content/browser/aboutHome-snippet1.png"),
    new Array("Firefox","8+","resource:///chrome/browser/skin/classic/aero/browser/Toolbar-inverted.png"),
    new Array("Internet Explorer","5-6","res://shdoclc.dll/pagerror.gif"),
    new Array("Internet Explorer","7+","res://ieframe.dll/info_48.png")
);
```

The module load each picture and check whether the load succeeded or failed.

## Screenshots

[[Images/information-gathering2.png|align=center]]

##Feedback

* **Firefox 15**: _1+,4+,8+_ 
* **IE6**: _IE 5-6_ 

##References