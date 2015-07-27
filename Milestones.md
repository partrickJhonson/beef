## VNC

Implement VNC style functionality in BeEF. 

This will allow real time monitoring of the hooked-browser’s view. That is, when the hooked browser follows a (onsite) link or enters content into input boxes it is viewed/monitored/recorded in the framework. 

The framework will have a proxy running on the loopback. When a browser connects to this proxy, the user can watch a playback or watch real-time with the user’s session. 

## Cross domain SQLi Scanner Milestone

Create a cross-domain SQLi scanner. The process will be similar to time delay sql injection detection.

The scanner will send a cross-domain HTTP request that will attempt to exploit a SQL injection vulnerability. The payload will delay the response from the server. Without breaking the same origin policy, the web browser can extrapolate the delay from the cross-domain server. 

Using the above technique repeatedly the scanner will test common locations on the application. 

This milestone includes stability and bug-fixing of the XssRays extension, that will be used as the delivery method and scanner of time-based blind SQLi payloads, and other tasks strictly related with the SQLi detection and exploitation mechanisms.

All the issues related to this milestone are outlined here:
[Cross domain time-based blind SQLi scanner](https://github.com/beefproject/beef/issues?sort=created&labels=Cross-domain+SQLi&direction=asc&state=open)

##Java Applet and Drone Milestone

Implement a malicious Java applet that uses code from JavaPayload by Michael Schierl. The first round has been implemented but is not functional. The applet will turn the machine running the browser into a drone under the control of BeEF.

After the successful deployment of a drone, the framework can send instructions to:

 * Download and execute file
 * DNS Spoof ()
 * Inject BeEF Hooks into HTTP traffic (possibly just injecting google-analytics.com)

Issues for this milestone are detailed [here](https://github.com/beefproject/beef/issues?sort=created&labels=Java+Applet&direction=asc&state=open)
and [here](https://github.com/beefproject/beef/issues?labels=RFC1918+Hijack&sort=created&direction=asc&state=open&page=1)

## MSF Integration and IPEC Tunnel Milestone

This milestone covers the outstanding MSF bugs and the MSF integration unit tests. It also includes wrapping MSF exploits in an IPEC tunnel. 

Currently, The MSF bridge lists all browser related exploits under one category in BeEF. Our target enhancements for this particular area include adding more intelligence to the exploit viewing and awareness to metadata such as OS target system, exploit options and exploit rating. This gives BeEF users the ability to quickly choose a good exploit that suites a specific target using the data that is already there in MSF exploits metadata and BeEF database.

Additionally, by adding IPEC tunneling, BeEF listens on a localhost port, tunnels anything it receives over http to the target's browser. With the browser hooked to BeEF, it translates the incoming IPEC traffic and directs to the target's Intranet.  Once this is working, BeEF could fire MSF exploits at the local port and have them hit a secure intranet target that maybe not even allowed to connect to the internet! Similar to how the proxy works, but in this case every byte coming in on the listening port is translated into JS byte array, passed to a hooked browser which reassembles them and then fires the data stream at the another target deeper into the network.


## Obfuscation Milestone

With obfuscation ALL traffic between the BeEF server and the hooked browser goes via the network stack. This means it is all obfuscated and un-obfuscated without the rest of the framework components knowing about it.

What we want is to have obfuscation extensions that can be used with the framework. These could be specified in the config file. They could even be chained. For example, one that is focused on compression and then one that obfuscates the data more. Also, there are plans to have the framework communicate using DNS tunnelling. 

A high level architecture of where the Obfuscation extension will have place in the BeEF framework is the following:
![Obfuscation high-level overview](http://antisnatchor.com/BeEF-images/CommunicationServerClient.png)

The API will look something like the below. We will need to consider these more.
GetBootStrapJS (Extension) - This is the method the framework uses to get the JS from the extension for the initial communication with the (soon to be) hooked browser.
GetSessionID (Extension) - This is the method the framework uses to get the session ID of the hooked browser. 
ObfuscateData (Ruby and JS) - Self explanatory 
UnObfuscateData (Ruby and JS) - Self explanatory

Implementation will occur in the following steps: 

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

All the steps are split in various issues, and can be found here:
https://github.com/beefproject/beef/issues?sort=created&labels=Obfuscation&direction=asc&state=open

## Social Engineering Milestone

Social engineering is considered one of the most used techniques by targeted attackers to penetrate large corporates, as well as being a very easy way to hack into small scale systems. All this makes it inevitable to use social engineering in penetration testing scenarios. Also, with the browser being the gateway to almost everywhere, it is important to focus on browser related social engineering attacks. The social engineering milestone aims to add a whole new factor to BeEF's exploitation arsenal, i.e. social engineering. This would be achieved by adding components for phishing and social media recon.

The phishing component of the framework would have the ability to clone portions of websites to convince a target to enter his credentials on it. Also, with the tab nabbing feature, it is possible to direct the target to a site will look interesting but long to read. After the user switches to another tab, the whole page is changed to resemble the login page of the phished website. Now the user might think that he has been logged out of his account and trip into entering his credentials in our phishing site.

On the other hand, the social media component plays a big role in acquiring information from different social networking websites. <Add text here>