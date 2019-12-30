So now, you have BeEF up and running, and you have hooked your first browser. You might be wondering what the next step is.

Your first step will often be to perform reconnaissance on the remote host. Which browser and plugins do they have running? Which website have you hooked?

This page will provide some information on how you may begin to go about this process.

## Browser Fingerprinting

When a browser is hooked, BeEF will automatically gather several pieces of information, including:

* Browser Name and Version
* Browser User Agent
* Plugins (including Java, ActiveX, VBS, Flash etc)
* If Adobe Flash Player is installed

##### Default Information Gathered from a Hooked Browser

[[Images/information-gathering1.png|align=center|width=500px]]

You can then use different plugins to gather more specific information on the browsers, for example:
* The [[Browser Fingerprinting|Module:-browser-fingerprint]] uses a number of custom URLs to identify the hooked browser. This can be useful if you are concerned that the user has changed their user agent.
* You can complete the list of plugins with the modules [[Detect Firebug|Module:-Detect-Firebug]], [[Detect Popup Blocker|Module:-Detect-Popup-Blocker]], [[Detect Google Desktop|Module:-Detect-Google-Desktop]] or [[Detect Unsafe ActiveX|Module:-Detect-Unsafe-ActiveX]].

##### Output from the [[Browser Fingerprinting|Module:-browser-fingerprint]] Module

[[Images/information-gathering2.png|align=center|width=400px]]

## Information Gathering on the System

BeEF enables you to gather information on the system of the hooked browser:
* Internet Explorer has permissions that allow system software detection (see [[Detect Softwares|Module:-Detect-Software]]) and even [[registry keys|Module:-Get-Registry-Keys]] (please note that attempting to use the registry keys module will prompt the browser's user for authorization).
* If the browser authorizes Java, the [[Get Internal IP|Module:-Get-Internal-IP]] module allows BeEF to detect the IP address of the system (don't worry, more fun network tricks  will be described [[later|Network-discovery]]).
* The [[Get System Info|Module:-Get-System-Info]] module can gather additional information on the system from a Java Applet including: Operating System details, Java JVM info, IP addresses, Processor/Memory specs, and more.
* It is also possible to retrieve the location of the user by using the [[Geolocation API|Module:-Get-Geolocation]] or by using [[a trick requesting Google maps|Module:-Get-Physical-Location]].
* The default Javascript API allows access to data stored [[in the clipboard|Module:-Get-Clipboard]].

##### Output from [[Get System Info|Module:-Get-System-Info]] Module

[[Images/module-get-systeminfo.png|align=center|width=500px]]


## User Behaviour Fingerprinting

A hooked browser allows BeEF to discover information on the behaviour of the user:
* Utilising some Javascript tricks, it is possible to detect if the browser has already visited [[a given URL|Module:-Detect-Visited-URL]] or [[a given domain|Module:-Get-Visited-Domains]].
* The [[Detect Social Networks|Module:-Detect-Social-Networks]] module can identify if the user of the hooked browser has a current session on Facebook, Twitter, or Gmail.
* The [[Detect TOR|Module:-Detect-TOR]] module can identify if the user of the hooked browser is currently using TOR.

##### Output from [[Detect Social Networks|Module:-Detect-Social-Networks]] Module:

[[Images/module-detect-social-network.png|align=center|width=500px]]

***
[[Previous|Interface]] | [[Next|Social-Engineering]]