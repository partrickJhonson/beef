With obfuscation ALL traffic between the BeEF server and the hooked browser goes via the network stack. This means it is all obfuscated and un-obfuscated without the rest of the framework components knowing about it.

What we want is to have obfuscation extensions that can be used with the framework. These could be specified in the config file. They could even be chained, for example, one that is focused on compression and then one that obfuscates the data more. Also, there are plans to have the framework communicate using DNS tunnelling. Whilst that functionality isn't in the code base yet we need to plan for it.

The API will look something like the below. We will need to consider these more.
GetBootStrapJS (Extension) - This is the method the framework uses to get the JS from the extension for the initial communication with the (soon to be) hooked browser.
GetSessionID (Extension) - This is the method the framework uses to get the session ID of the hooked browser. 
ObfuscateData (Ruby and JS) - Self explanatory 
UnObfuscateData (Ruby and JS) - Self explanatory

What I propose is the following steps. 

Step One:
Implement the unit test wrapper that will be used with all the obfuscation extensions. 

Step Two:
Move the current functionality into an obfuscation extension and ensure the framework is still fully functional. Of course, this will need to work with the unit tests generated from the wrapper in step one. The session id needs to controlled by the extension code. This might be custom to each extension.  

Step Three:
Implement a simple base64 obfuscation extension and the associated unit tests. This means that all data (other than the BootStrapJS) moving between the BeEF server and the hooked browser will be base64 and nothing else. This extension will not use evercookie or any cookies at all. 

Step Four:
Implement URL randomisation and an extension that solely communicates using it. This means that there are no parameters and no post requests. 

Step Five:
Implement a minify obfuscation extension and the associated unit tests. 

Step Six:
Update this Wiki page.
