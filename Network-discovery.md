_With Javascript hacks, it is possible to launch network attacks through a hooked browser._

## Get Internal IP Address

The [[Get Internal IP Address|Module:-Get-Internal-IP]] module uses a Java applet to gather information on IP address of the computer. From this IP address, it becomes possible to imagine the internal addressing plan and use the other modules.

[[Images/module-get-internal-ip.png|align=center]]

## Get Internal IP Address WebRTC

The [[Get Internal IP (WebRTC)|Module:-Get-Internal-IP-WebRTC]] module for Firefox and Chrome uses WebRTC to retrieve the IP address for each network interface. From these IP addresses, it becomes possible to imagine the internal addressing plan and uses the other modules.

## Get HTTP Servers

The Get HTTP Servers module loads favicon images from predictable paths (/favicon.ico, /favicon.png, /images/favicon.ico, /images/favicon.png) on specified IP address(es) to detect web servers on the zombie's local area network(s). From these IP addresses, it becomes possible to imagine the internal addressing plan and uses the other modules.

## Identify LAN Subnets

The Identify LAN Subnets module uses time-based XHR to determine whether any commonly used LAN IP addresses are in use on the zombie's local area network(s). From these IP addresses, it becomes possible to imagine the internal addressing plan and uses the other modules.

## Ping Sweep (Java)

Then, by using Java, it is possible to launch ping request and identify alive hosts on the network. This modules exists in two version, [[the default version|Module:-Ping-Sweep]] which directly uses Java API and [[the Java version|Module:-Ping-Sweep-(Java)]] which loads a Java applet.

[[Images/module-ping-sweep1.png|align=center]]

## Cross-Origin Scanner

The Cross-Origin Scanner sends CORS requests to a specified IP range and returns the IP address, port, HTTP status code, page title and page contents for each CORS enabled web server identified.

## DNS Enumeration

By playing with timers, it is possible to detect whether a given hostname exist or not with Firefox and Chrome. In the first case, the request will take longer as the DNS resolution will be done and then the TCP connection will start (and probably fail). In the second case, the DNS request will return an error quickly, thus the browser is able to detect that there is no such DNS entry.

See the corresponding [[BeEF module|Module:-DNS-Enumeration]]

## Port Scanning

Now that we know the IP address of the hooked system and several hostnames, it would be interesting to launch port scanning. Happily several researchers have found that it is possible to use the same timing hack to scan ports by loading images into the browser with Firefox and Chrome. This attack was included in the [[Port Scanner|Module:-Port-Scanner]] module.

[[Images/module-port-scanner2.png|align=center]]

## Network Fingerprinting

The [[Network Fingerprinting module|Module:-Fingerprint-Network]] uses URL of default images to fingerprint the devices used on the network. It embedds a list of default pictures for Web servers (apache, IIS) and network devices (Linksys NAS, printers...) and check if one of this picture is available.

[[Images/module-network-fingerprint2.png|align=center|width=400px]]

## Remote CSRFs

CSRF is still a vulnerabilty seldom taken into account by developers while it can have serious impact. BeEF includes a lot of CSRF modules, especially targeting personal routes (Linksys, Dlink...). Happily, we just detected one of those routers when fingerprinting the network during the previous step. Most of CSRF attacks allows modifying the admin password however several can be used to open external ports on the box.

You can see the list of CSRF modules in the [[module|BeEF-modules]] page.

## IRC NAT Pinning

By simulating IRC communication from the browser, it is possible to deceive firewall for opening TCP ports. This hack is called [[NAT Pinning|http://samy.pl/natpin/]] and it is included in the BeEF [[IRC NAT Pinning module|Module:-IRC-NAT-Pinning]]. You can find more information and exemple on the [BeEF's blog](http://blog.beefproject.com/2012/07/opening-closed-ports-on-nat-device-and.html).

***
[[Previous|Social-Engineering]] | [[Next|Metasploit]]