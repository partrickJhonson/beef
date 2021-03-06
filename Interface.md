## Introduction
BeEF's interface organises a collection of hooked browsers, commands and results. The below guide has been created to assist you in navigating BeEF and familiarising yourself with the types of exploits available.

#### Table of Contents

* [Login](#login)
* [Home Page](#home-page)
* [Hooked Browsers](#hooked-browsers)
* [Command Tab](#command-tab)


## Login
First when you arrive on the BeEF web server (default is [http://localhost:3000/ui/panel](http://localhost:3000/ui/panel) if you haven't customised as in [Configuration](https://github.com/beefproject/beef/wiki/Configuration)), you'll see the login page :

<p align="center">
[[Images/interface-login.png|align=center]]
</p>

Please enter the username and password that you configured in the config.yaml file in the beef directory.


## Home Page

The home page will look like this :

[[Images/interface-home.png|align=center]]

Starting out, you will see that there are no browsers hooked and very few options available to you so the first step is to hook a browser, for example by using one of the demo page as described in the "Getting Started" tab.

## Hooked Browsers

After a successful hook, you will quickly see a new hooked browser in the beef menu :

[[Images/interface-hooked.png|align=center]]

By clicking on the new hooked browser, you will see a new tab "Current Browser" on the left :

[[Images/interface-hooked2.png|align=center]]

This new tab presents details on the browser, the hooked page and the hooked host but it provides also a new tab menu dedicated to the selected browser.

## Command Tab

Go then directly to the "Command" tab :

[[Images/interface-command.png|align=center]]

You will see bullets with different colors before each module. Internally, BeEF detects which browser you hooked and knows which modules are working on each browser :

* Green: The command module works against the target and should be invisible to the user
* Orange: The command module works against the target, but may be visible to the user
* Grey: The command module is yet to be verified against this target
* Red: The command module does not work against this target

Note that the traffic light system indicates whether the command module works on the zombie browser and underlying operating system in use by the zombie browser; however, the module may have other requirements, such as the presence of third-party browser addons such as Flash, may require execution within a privileged zone, such as `chrome://`, or may require the presence of third-party libraries such as the [PhoneGap API](https://phonegap.com/).

For example, let's try to get the internal IP of the hooked browser. Select "Get Internal IP" in the Host category and click on "Execute" (this module should work on most browsers if the host has Java installed). After few seconds you will see a new command in the history part :

[[Images/interface-command2.png|align=center]]

If you now go to the "Logs" tab, you will see two pieces of information:

* The browsers joined the zombie horde
* You launched the "Get Internal IP" on the hooked browser

[[Images/interface-log.png|align=center]]

You can also see that the main tab "Logs" has now a list on all actions completed on all browsers :

[[Images/interface-log2.png|align=center]]

The last tabs are dedicated to [[Tunneling Proxy|Tunneling]] and [[Xss Rays|Xss-Rays]] which will be addressed later on in this wiki.

***

[[Configuration|Configuration]] | [[Information Gathering|Information-Gathering]]