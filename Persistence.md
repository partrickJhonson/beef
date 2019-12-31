## Introduction
These four modules have been developed to keep maintain persistence on hooked browsers.

## Old School : Pop under the browser

[[Old School |Module:-Create-Pop-Under]] will create a pop-up window under the browser which will open an empty BeEF page. Old school but it still works!

## Dirty : Ask for Confirmation for Closing the Tab

The [[Dirty|Module:-Confirm-Close-Tab]] module will ask the user to confirm that they want to close this tab again and again and again. Dirty!
<p align=center>
[[Images/module-confirm-close-tab1.png|align=center]]
</p>

## Stealth : Redirect Links to Foreground iFrames

[[Stealth|Module:-Create-Foreground-iFrame]] will rewrite all the links in the webpage to avoid leaving the current page. Instead, the module will load the target URL in a 100% foreground iFrame. Stealth but the URL still does not change!

## Clean : Man In The Browser

[[Clean|Module:-Man-In-The-Browser]] will launch a "man-in-the-browser" hack : the module loaded will handle every click on a new link. For links in the same domain, it will make an AJAX request and load the new page instead of the old one and add the page in the history, there is no difference for the user with a classical load but the browser is still hooked. Due to the Same Origin Policy, it is not possible to have the same behavior on other domain, so in this case, the module will open the link in a new tab. 

***

[[Previous|Xss-Rays]] | [[Next|BeEF-RESTful-API]]