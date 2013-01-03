##Summary
* **Objective**: Asks the user for their username and password using a floating div.
* **Authors**: pwndizzle, vt, xntrik
* **Browsers**: Safari, Firefox, Chrome, Opera (User is notified)
* **Paramters** :
  * **Dialog Type** : Type of dialog box : Facebook, Linked In or Generic
  * **Backing** : Color of the background (Grey or Clear)
  * **Custom Generic Logo** : URL of the logo for generic dialog type
* [Code](https://github.com/beefproject/beef/tree/master/modules/social_engineering/pretty_theft)

##Internal Working

This module will just print a dialog box imitating Facebook or Linked and asking for credentials. Nothing complex here, [the code ](https://github.com/beefproject/beef/blob/master/modules/social_engineering/pretty_theft/command.js) is a bit long due to styles modification but it is not very complex to read.

## Screenshots

_Command_ :
[[Images/module-prettytheft1.png|align=center]]

_Facebook box_ :
[[Images/module-prettytheft2.png|align=center]]

_LinkedIn box (bug here)_ :
[[Images/module-prettytheft3.png|align=center]]

_Generic box with BeEF logo_ :
[[Images/module-prettytheft4.png|align=center]]

_Result_ :
[[Images/module-prettytheft5.png|align=center]]

## Feedback

* Works very well on Chrome. Linked In logo requires access to linkedin website (explaining the picture bug).