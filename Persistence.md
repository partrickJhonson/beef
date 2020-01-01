## Introduction
BeEF has four modules that have been developed to help maintain persistence on hooked browsers.

#### Table of Contents

* [Old School Module](#old-school-module)
* [Dirty Module](#dirty-module)
* [Stealth Module](#stealth-module)
* [Clean Module](#clean-module)

## Old School Module 

The [[Old School|Module:-Create-Pop-Under]] module will create a pop-up window underneath the victim's browser. This window will open an empty BeEF page. An old school technique but it still works!

## Dirty Module

The [[Dirty|Module:-Confirm-Close-Tab]] module will ask the user to confirm that they want to close this tab again and again and again. Dirty!

<p align=center>
[[Images/module-confirm-close-tab1.png|align=center]]
</p>

## Stealth Module

The [[Stealth|Module:-Create-Foreground-iFrame]] module will rewrite all the links on the web-page causing them to load the target URL in a 100% foreground iFrame. This means that the victim sees the page they were expecting to be redirected to, but the URL still does not change!

## Clean Module

The [[Clean|Module:-Man-In-The-Browser]] module launches a "man-in-the-browser" hack. It listens for and handles any click on a link. 

For links within same domain, [[Clean|Module:-Man-In-The-Browser]] will make an AJAX request and load the new page instead of the old one and then add the page into the browser's history. There will be no visible difference to the victim. The page will load in the typical fashion but the browser is still hooked. 

The Same Origin Policy prevents this behaviour on other domains, so in the event that the victim navigates to a domain that is not within the same domain, [[Clean|Module:-Man-In-The-Browser]] will open the requested web-page in a new tab. 

***

[[XSS Rays|Xss-Rays]] | [[BeEF RESTful API|BeEF-RESTful-API]]