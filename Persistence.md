Today, four modules have been developed to try keeping a browser hooked.

## Old School : Pop under the browser

[[This module|Module:-Create-Pop-Under]] will create a pop window under the browser which open an empty BeEF page. Old school but it still works !

## Dirty : Ask to confirmation for closing the tab

[[This module|Module:-Confirm-Close-Tab]] ask the user to confirm that he want to close this tab again and again and again. Dirty !

[[Images/module-confirm-close-tab1.png|align=center]]

## Stealth : Redirect links to Foreground iframes

[[This module|Module:-Create-Foreground-iFrame]] will rewrite all the links in the webpage to avoid leaving the current page. Instead, the module will load the target URL in a 100% foreground iframe. Stealth but the URL still does not change !

## Clean : Man In The Browser

[[This module|Module:-Man-In-The-Browser]] launch a great man in the browser hack : the module loaded will handled every click on a new link. For links in the same domain, it will make an AJAX request and load the new page instead of the old one and add the page in the history, there is no difference for the user with a classical load but the browser is still hooked. Due to the Same Origin Policy, it is not possible to have the same behavior on other domain, so in this case, the module will open the link in a new tab. 