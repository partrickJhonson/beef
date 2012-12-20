# Interface

## Login

First when you arrive on the BeEF web server (probably at [http://localhost:3000/ui/panel](http://localhost:3000/ui/panel) if you starts with BeEF), you'll see the login page :

[[Images/interface-login.png|align=center]]

By default, login and passwords are beef/beef.

## Home Page

The home page look like this :

[[Images/interface-home.png|align=center]]

So first, you will see that there is few actions possible as you do not have any browser hooked. So you need to hook a browser, for example by using one of the demo page ( url should be [http://localhost:3000/demos/basic.html](http://localhost:3000/demos/basic.html) and [http://localhost:3000/demos/butcher/index.html](http://localhost:3000/demos/butcher/index.html) )


## Hooked browsers

After a successful hook, you will quickly seen a new hooked browser in the beef menu :

[[Images/interface-hooked.png|align=center]]

By clicking on the new hooked browser, you will select theis browser as the current browser and you will see a new tab "Current Browser" on the left :

[[Images/interface-hooked2.png|align=center]]

This new tab presents details on the browser, the hooked page and the hooked host but it provides also a new tab menu dedicated to the selected browser.

## Command Tab

Go then directly to the command Tab :

[[Images/interface-command.png|align=center]]

You will see bullets with different colors before each module. Internally, BeEF detects which browser you hooked and knows which modules are working on each browser :

* Green : It works on the browser selected. Go !
* Orange : It will work but the user may detect it. Notice that it can be legitimate for example for social engineering modules
* Red : it won't work on this browser. But you still can try !

For example, let's try to get the internal IP of the hooked browser. Select "Get Internal IP" in the Host category and click on "Execute" (this module should work on most browsers if the host has Java installed). After few seconds you will see a new command in the history part :

[[Images/interface-command2.png|align=center]]

If you now go to the "Logs" tab, you will see two informations :

* The browsers joined the zombie horde
* You launched the "Get Internal IP" on the hooked browser

[[Images/interface-log.png|align=center]]

You can also see that the main tab "Logs" has now a list on all actions done on all browsers :

[[Images/interface-log2.png|align=center]]

Last tabs are dedicated to [[Tunneling Proxy|Tunneling]] and [[Xss Rays|Xss-Rays]] which will be addressed in next parts of this documentation.

***

[[Previous|Configuration]] | [[Next|Information-Gathering]]