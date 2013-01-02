When you have hooked a browser, you can modify the whole page and cause different actions (redirection...), so there are a lot of possibilities for social engineering attacks. This page will try to sum them up.

# Ask for crendentials

Simplest attacks are often the most efficient ones, so you can just ask for it to the user with different modules :

* [[The Pretty Theft|Module:-Pretty-Theft]] module prints a simple message to the user for requiring login and password and explaining that the session has timed out
* [[The Simple Hijacker|Module:-Simple-Hijacker]] module proposes several social engineering templates and prompt them to the user when he will click on a link on the page.

[[Images/module-prettytheft1.png|align=center]]

# Redirect to another page

You may also uses BeEF modules to redirect to external pages :

* By using the basic [[rediret browser|Module:-Redirect-Browser]] module, you can redirect the hooked page to any other page. Note that it may be weird for the user to be redirect and that you will loose the zombie. To avoid loosing the browser from BeEF, you can also use the [[rediction module with iframe|Module:-Redirect-Browser-(iFrame)]] which will open a 100% iframe to the given url.
* You can also use the great [[tabnabbing module|Module:-TabNabbing]] : this module detect when the user loose focus on the current tab and modify the whole page to load the given URL in an iframe at this time. When the use comes back to the tab, he will directly see the new web page.

# Chrome Extensions

[TODO]

# Other

***
[[Previous|Information-Gathering]] | [[Next|Network-discovery]]