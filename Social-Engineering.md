Once BeEF has hooked a browser, it can modify and/or send content directly to the viewport or other open tabs. This functionality allows you to craft and perform sophisticated social engineering attacks. 

# Ask for Credentials

Simple attacks are often the most efficient ones. BeEF comes with several command modules that present the target with familiar interfaces requesting credentials:

* [[The Pretty Theft|Module:-Pretty-Theft]] module prints a simple message to the user requiring login and password, explaining that the session has timed out. It has a number of presets that imitate popular social network/marketplace themes.
* [[The Simple Hijacker|Module:-Simple-Hijacker]] module allows you to load a number of common pop-ups when a user clicks any link on their current page. Pop-up templates include certificate warnings, standard alert style prompts, and credit card payment forms.
* [[Clippy|Module:-Clippy]] is a module that create a small browser assistant which propose browser updates.

_A Sample Pretty Theft Pop-up:_ 

[[Images/module-prettytheft1.png|align=center]]

# Redirect to Another Page

A number BeEF modules exist that allow you to redirect to external pages:

* The [[Redirect Browser|Module:-Redirect-Browser]] module can redirect the hooked page to any other page. 
  * Please note that a spontaneous redirect without any action from the user may cause them to immediately close the zombie. 
  * To avoid losing the zombie from BeEF, the [[Redirect Browser (iFrame)|Module:-Redirect-Browser-(iFrame)]] sub-module will create a full viewport iFrame which redirects to the specified URL.
* The [[TabNabbing|Module:-TabNabbing]] module will detect when the user loses focus on the current tab and modify it in the background. When the user comes back to the tab, they will be viewing a full viewport iFrame containing the contents of the specified URL.

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

# Other Notable Social Engineering Modules

* The [[ClickJacking|Module:-Clickjacking]] module which allow a custom clickjacking attack by giving the URL and  offset on the target page :

[[Images/module-clickjacking1.png|align=center]]

***
[[Previous|Information-Gathering]] | [[Next|Network-discovery]]