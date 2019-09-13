_Now, you have BeEF installed and launched, you have hooked your first browser. What's the next step ?_

_The first step is often to gather information on the remote host : which browser and plugins, which website hooked..._

## Browser fingerprinting

When a browser is hooked, BeEF will automatically gather several pieces of information on the hooked browser :

* Browser name and version
* Browser User Agent
* Plugins (including Java, ActiveX, VBS, Flash...)
* Windows size

_Default information on the hooked browser gathered by BeEF_ :

[[Images/information-gathering1.png|align=center|width=500px]]

You can then use different plugins to gather more detailed information on the browsers :
* The module [[Browser Fingerprinting|Module:-browser-fingerprint]] uses custom url to identify the browser. It can be useful if the user has changed its user agent.
* You can complete the list of plugins with the modules [[Detect Firebug|Module:-Detect-Firebug]], [[Detect popup blocker|Module:-Detect-popup-blocker]], [[Detect Google Desktop|Module:-Detect-Google-Desktop]], [[Detect unsafe ActiveX|Module:-Detect-Unsafe-ActiveX]]...

_Result of the browser fingerprinting module_ :

[[Images/information-gathering2.png|align=center|width=400px]]

## Information gathering on the system

By using several modules, you can also gather information on the system of the hooked browser :
* Internet Explorer has permissive restrictions allowing to detect softwares installed (module [[Detect Softwares|Module:-Detect-Software]]) and even [[registry keys|Module:-Get-Registry-Keys]] (caution, in this case the user will be prompted with an authorization message).
* If the browsers authorize Java, the module [[Get Internal IP|Module:-Get-Internal-IP]] allows to detect the IP address of the system (funnier tricks with the network will be described [[later|Network-discovery]])
* The module [[Get System Info|Module:-Get-System-Info]] uses also a Java Applet to gather detailed information on the system : operating system details, Java JVM details, IP addresses, amount of memory...
* It is also possible to retrieve the location of the user whether by using the [[geolocation API|Module:-Get-Geolocation]] or by using [[a trick requesting Google maps|Module:-Get-Physical-Location]].
* The default javscript API allows of course, to get the data stored [[in the clipboard|Module:-Get-Clipboard]].

_Result of Get System Info module :_
[[Images/module-get-systeminfo.png|align=center|width=500px]]


## User's behaviour fingerprinting

The hooked browser also allows to discover several information on the behaviour of the user :
* By using javascript tricks, it is possible to detect if the browser has already visited [[a given URL|Module:-Detect-Visited-URL]] or [[a given domain|Module:-Get-Visited-Domains]].
* Two modules can be used to know if the user is logged [[on social networks|Module:-Detect-Social-Networks]], and if the user [[uses TOR|Module:-Detect-TOR]].

[[Images/module-detect-social-network.png|align=center|width=500px]]

***
[[Previous|Interface]] | [[Next|Social-Engineering]]