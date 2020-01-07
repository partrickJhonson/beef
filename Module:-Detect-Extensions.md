## Summary

* **Objective**: Detect extensions on Chrome and Firefox
* **Authors**: koto, bcoles, nbblrr
* **Browsers**: Chrome < 18, Firefox < 50

* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/detect_extensions)


## Internal Working

Loops over hardcoded extension IDs in Chrome and Firefox to detect which ones are installed.

## Feedback

* Apparently it has been blocked recently by Chrome : it is not working on my Chrome 22 with error : _Denying load of chrome-extension://bhmmomiinigofkjcapegjjndpbikblnp/manifest.json. Resources must be listed in the web_accessible_resources manifest key in order to be loaded by pages outside the extension._ This has been corrected through whitelisting since Chrome 19 (see [here](http://code.google.com/p/chromium/issues/detail?id=118693))
* Firefox hack still works on Firefox 17.

## References

* [Intro to Chrome Hacking : Fingerprinting](http://blog.kotowicz.net/2012/02/intro-to-chrome-addons-hacking.html)
* [Sparse Bruteforce Addon Detection](http://www.skeletonscribe.net/2011/07/sparse-bruteforce-addon-scanner.html)
* [Issue 118693: Chrome leaks installed extensions to all websites](http://code.google.com/p/chromium/issues/detail?id=118693)
* [I know what you've got (Firefox Extensions)](http://jeremiahgrossman.blogspot.fr/2006/08/i-know-what-youve-got-firefox.html) By Jeremiah Grossman