## Introduction

Once BeEF has hooked a browser, it can modify and/or send content directly to the viewport or other open tabs. This functionality allows you to craft and perform sophisticated social engineering attacks. 

#### Table of Contents

* [Ask for Credentials](#ask-for-credentials)
* [Redirect to Another Page](#redirect-to-another-page)
* [Chrome/Firefox Extensions](#chromefirefox-extensions)
* [Clickjacking](#clickjacking)

## Ask for Credentials

Simple attacks are often the most efficient ones. BeEF comes with several command modules that present the target with familiar interfaces requesting credentials:

* [[The Pretty Theft|Module:-Pretty-Theft]] module prints a simple message to the user requiring login and password, explaining that the session has timed out. It has a number of presets that imitate popular social network/marketplace themes.
* [[The Simple Hijacker|Module:-Simple-Hijacker]] module allows you to load a number of common pop-ups when a user clicks any link on their current page. Pop-up templates include certificate warnings, standard alert style prompts, and credit card payment forms.
* [[Clippy|Module:-Clippy]] is a module that create a small browser assistant which propose browser updates.

##### A Pretty Theft Pop-up Template:
<p align=center>
[[Images/module-prettytheft1.png|align=center]]
</p>

## Redirect to Another Page

A number BeEF modules exist that allow you to redirect to external pages:

* The [[Redirect Browser|Module:-Redirect-Browser]] module can redirect the hooked page to any other page. 
  * Please note that a spontaneous redirect without any action from the user may cause them to immediately close the zombie. 
  * To avoid losing the zombie from BeEF, the [[Redirect Browser (iFrame)|Module:-Redirect-Browser-(iFrame)]] sub-module will create a full viewport iFrame which redirects to the specified URL.
* The [[TabNabbing|Module:-TabNabbing]] module will detect when the user loses focus on the current tab and modify it in the background. When the user comes back to the tab, they will be viewing a full viewport iFrame containing the contents of the specified URL.

## Chrome/Firefox Extensions

Using BeEF it is possible to get a user to install a malicious browser extension:

* The [[Fake Flash Update|Module:-Fake-Flash-Update]] module prompts the hooked browser's user to install a flash update. Instead of installing a Flash update, a browser extension will be installed that can communicate with BeEF and provide access to far more information than is available by default.
  * If the extension were installed in Chrome, for example, BeEF could run the following modules:
    * [[Get All Cookies|Module:-Get-All-Cookies]]
    * [[List Chrome Extensions|Module:-Get-Chrome-Extensions]]
    * [[Grab Google Contacts from Logged in User|Module:-Grab-Google-Contacts]]
    * [[Inject BeEF in All Tabs|Module:-Inject-BeEF]] 
    * [[Execute Arbitrary Javascript Code|Module:-Execute-On-Tab]]
    * [[Taking Screenshots|Module:-Screenshot]]
    * [[Send Gvoice SMS|Module:-Send-Gvoice-SMS]]

##### Fake Flash Update Pop-up:
<p align=center>
[[Images/module-fake-flash-update2.png|align=center]]
</p>

## Clickjacking

BeEF contains a module that enables clickjacking attacks in a hooked browser:

* The [[Clickjacking|Module:-Clickjacking]] module will create an iFrame which follows the users cursor around the page, displaying the content at the specified URL.

***
[[Information Gathering|Information-Gathering]] | [[Network Discovery|Network-discovery]]