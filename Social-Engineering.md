When you have hooked a browser, you can modify the whole page and cause different actions (redirection...), so there are a lot of possibilities for social engineering attacks. 

# Ask for Credentials

Simplest attacks are often the most efficient ones, you can simply ask users for their credentials using different modules :

* [[The Pretty Theft|Module:-Pretty-Theft]] module prints a simple message to the user for requiring login and password and explaining that the session has timed out
* [[The Simple Hijacker|Module:-Simple-Hijacker]] module proposes several social engineering templates and prompt them to the user when he will click on a link on the page.
* [[Clippy|Module:-Clippy]] is a module that create a small browser assistant which propose browser updates.

[[Images/module-prettytheft1.png|align=center]]

# Redirect to Another Page

You may also use BeEF modules to redirect to external pages :

* By using the basic [[rediret browser|Module:-Redirect-Browser]] module, you can redirect the hooked page to any other page. Note that it may be weird for the user to be redirected and that you will lose the zombie. To avoid losing the browser from BeEF, you can also use the [[rediction module with iframe|Module:-Redirect-Browser-(iFrame)]] which will open a 100% iframe to the given url.
* You can also use the great [[tabnabbing module|Module:-TabNabbing]] : this module will detect when the user loses focus on the current tab and modify the whole page to load the given URL in an iframe at this time. When the use comes back to the tab, he will directly see the new web page.

# Chrome/Firefox Extensions

By requiring the user to install [[a fake flash update|Module:-Fake-Flash-Update]], it is possible to install a malicious Firefox/Chrome extension. Once installed this extension can communicate directly with BeEF and have access to much more information than code in the hooked browser.

[[Images/module-fake-flash-update2.png|align=center]]

By using Chrome extensions module, it is possible to use the malicious extension to :
* [[Get all cookies|Module:-Get-All-Cookies]]
* [[List chrome extensions|Module:-Get-Chrome-Extensions]]
* [[Grab Google contacts|Module:-Grab-Google-Contacts]] of the logged in Google account
* [[Inject BeEF|Module:-Inject-BeEF]] in all tabs
* [[Execute javascript code in a new tab|Module:-Execute-On-Tab]]
* [[Take screenshot|Module:-Screenshot]]
* [[Send Gvoice SMS|Module:-Send-Gvoice-SMS]]

# Other

* There is also a nice [[clickjacking|Module:-Clickjacking]] module which allow custom clickjacking attack by giving the URL and  offset on the target page :

[[Images/module-clickjacking1.png|align=center]]

***
[[Previous|Information-Gathering]] | [[Next|Network-discovery]]