_So now, you have BeEF up and running, and you have hooked your first browser. You might be wondering what the next step is._

_Your first step will often be to perform reconnaissance on the remote host. Which browser and plugins do they have running? Which website have you hooked?_

_This page will provide some information on how you may begin to go about this process._

## Browser Fingerprinting

When a browser is hooked, BeEF will automatically gather several pieces of information on the hooked browser:

* Browser Name and Version
* Browser User Agent
* Plugins (including Java, ActiveX, VBS, Flash...)
* Windows Size

_Default information on the hooked browser gathered by BeEF:_

[[Images/information-gathering1.png|align=center|width=500px]]

You can then use different plugins to gather more detailed information on the browsers:
* The module [[Browser Fingerprinting|Module:-browser-fingerprint]] uses a number of custom URLs to identify the hooked browser. It can also be useful if the user changes their user agent.
* You can complete the list of plugins with the modules [[Detect Firebug|Module:-Detect-Firebug]], [[Detect Popup Blocker|Module:-Detect-Popup-Blocker]], [[Detect Google Desktop|Module:-Detect-Google-Desktop]], [[Detect Unsafe ActiveX|Module:-Detect-Unsafe-ActiveX]]...

_Result of the Browser Fingerprinting Module:_

[[Images/information-gathering2.png|align=center|width=400px]]

## Information Gathering on the System

By using several modules, you can also gather information on the system of the hooked browser :
* Internet Explorer has permissive restrictions allowing to detect softwares installed (module [[Detect Softwares|Module:-Detect-Software]]) and even [[registry keys|Module:-Get-Registry-Keys]] (caution, in this case the user will be prompted with an authorization message).
* If the browsers authorize Java, the module [[Get Internal IP|Module:-Get-Internal-IP]] allows to detect the IP address of the system (funnier tricks with the network will be described [[later|Network-discovery]])
* The module [[Get System Info|Module:-Get-System-Info]] uses also a Java Applet to gather detailed information on the system : operating system details, Java JVM details, IP addresses, amount of memory...
* It is also possible to retrieve the location of the user whether by using the [[geolocation API|Module:-Get-Geolocation]] or by using [[a trick requesting Google maps|Module:-Get-Physical-Location]].
* The default javscript API allows of course, to get the data stored [[in the clipboard|Module:-Get-Clipboard]].

_Result of Get System Info Module:_

[[Images/module-get-systeminfo.png|align=center|width=500px]]


## User's behaviour fingerprinting

The hooked browser also allows to discover several information on the behaviour of the user :
* By using javascript tricks, it is possible to detect if the browser has already visited [[a given URL|Module:-Detect-Visited-URL]] or [[a given domain|Module:-Get-Visited-Domains]].
* Two modules can be used to know if the user is logged [[on social networks|Module:-Detect-Social-Networks]], and if the user [[uses TOR|Module:-Detect-TOR]].

[[Images/module-detect-social-network.png|align=center|width=500px]]

***
[[Previous|Interface]] | [[Next|Social-Engineering]]