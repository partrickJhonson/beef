This module launches a great Man-In-The-Browser hack : the module loaded will handle every click on a new link. For links in the same domain, it will make an AJAX request and load the new page instead of the old one and add the page in the history, there is no difference for the user with a classical load but the browser is still hooked. Due to the Same Origin Policy, it is not possible to have the same behavior on other domain, so in this case, the module will open the link in a new tab. 

Note that this module will cease working if the user manually enters a new URL in the address bar.
