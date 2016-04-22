_With JavaScript hacks, it is possible to launch network attacks through a hooked browser._

## Get Internal IP Address

Two modules exist to retrieve the IP addresses in use by the zombie browser host system. From these IP addresses it becomes possible to imagine the internal network addressing plan and use the other modules.

The [[Get Internal IP (WebRTC)|Module:-Get-Internal-IP-WebRTC]] module for Firefox and Chrome uses WebRTC to retrieve the IP address for each network interface.

![Get Internal IP Address WebRTC](https://cloud.githubusercontent.com/assets/434827/5973009/0a055c62-a8b7-11e4-82fd-96e726f8a60a.png)

The [[Get Internal IP Address|Module:-Get-Internal-IP]] module uses a Java applet to retrieve the IP address. Since Java introduced click-to-play the user must allow the unsigned Java applet to run.

[[Images/module-get-internal-ip.png|align=center]]

## Identify LAN Subnets

The Identify LAN Subnets module uses time-based XHR to determine whether any commonly used LAN IP addresses are in use on the zombie's local area network(s). From these IP addresses, it becomes possible to imagine the internal addressing plan and use the other modules. This module works only with Firefox and Chrome.

![Identify LAN Subnets](https://cloud.githubusercontent.com/assets/434827/5973018/2059b59e-a8b7-11e4-9e67-17b7ea0b75bb.png)

## Get HTTP Servers

The Get HTTP Servers module loads favicon images from predictable paths (/favicon.ico, /favicon.png, /images/favicon.ico, /images/favicon.png) on specified IP address(es) to detect web servers on the zombie's local area network(s). From these IP addresses, it becomes possible to imagine the internal addressing plan and use the other modules. This module should be invisible to the user in Internet Explorer and Safari, however with other browsers the user may notice if any of the scanned hosts pop a 401 Authentication Required prompt.

![Get HTTP Servers](https://cloud.githubusercontent.com/assets/434827/5973022/330d4c78-a8b7-11e4-90e9-89260effd9c8.png)

## Ping Sweep

Then it is possible to launch ping request and identify alive hosts on the network. This modules exists in three versions.

The [[Ping Sweep|Module:-Ping-Sweep]] module uses time-based JavaScript XHR requests to identify live hosts. This module works only in Firefox.

The [[Ping Sweep (FF) module|Module:-Ping-Sweep-(FF)]] uses the Java API directly to send requests and time the response. This module works only in Firefox with Java installed.

The [[Ping Sweep (Java)|Module:-Ping-Sweep-(Java)]] which loads a Java applet. Since Java introduced click-to-play the user must allow the unsigned Java applet to run.

[[Images/module-ping-sweep1.png|align=center]]

## Cross-Origin Scanner (CORS)

The Cross-Origin Scanner (CORS) module sends CORS requests to a specified IP range and returns the IP address, port, HTTP status code, page title and page contents for each web server identified with a permissive CORS policy. This module should work on all modern browsers which support CORS.

![Cross-Origin Scanner](https://cloud.githubusercontent.com/assets/434827/5973004/ebd4b0b2-a8b6-11e4-9777-f5e3bb6377b7.png)

## Cross-Origin Scanner (Flash)

The Cross-Origin Scanner (Flash) module sends requests to a specified IP range using Flash and returns the IP address, port, page title and page contents for each web server identified with a permissive flash cross-origin policy. This module works only in Firefox and Chrome with Flash installed.

## DNS Enumeration

By playing with timers, it is possible to detect whether a given hostname exist or not with Firefox and Chrome. In the first case, the request will take longer as the DNS resolution will be done and then the TCP connection will start (and probably fail). In the second case, the DNS request will return an error quickly, thus the browser is able to detect that there is no such DNS entry.

See the corresponding [[BeEF module|Module:-DNS-Enumeration]]

## Port Scanning

Now that we know the IP address of the hooked system and several hostnames, it would be interesting to launch port scanning. Happily several researchers have found that it is possible to use the same timing hack to scan ports by loading images into the browser with Firefox and Chrome. This attack was included in the [[Port Scanner|Module:-Port-Scanner]] module.

[[Images/module-port-scanner2.png|align=center]]

## Network Fingerprinting

The [[Network Fingerprinting module|Module:-Fingerprint-Network]] uses URL of default images to fingerprint the devices used on the network. It embedds a list of default pictures for Web servers (apache, IIS) and network devices (Linksys NAS, printers...) and check if one of this picture is available. This module should work in all browsers. The user may notice if any of the scanned hosts pop a 401 Authentication Required prompt.

[[Images/module-network-fingerprint2.png|align=center|width=400px]]

## Remote CSRFs

CSRF is still a vulnerability seldom taken into account by developers while it can have serious impact. BeEF includes a lot of CSRF modules, especially targeting personal routes (Linksys, Dlink...). Happily, we just detected one of those routers when fingerprinting the network during the previous step. Most of CSRF attacks allows modifying the admin password however several can be used to gain a reverse shell or open external ports on the box.

You can see the list of CSRF modules in the [[module|BeEF-modules]] page.

## IRC NAT Pinning

By simulating IRC communication from the browser, it is possible to deceive firewall for opening TCP ports. This hack is called [[NAT Pinning|http://samy.pl/natpin/]] and it is included in the BeEF [[IRC NAT Pinning module|Module:-IRC-NAT-Pinning]]. You can find more information and exemple on the [BeEF's blog](http://blog.beefproject.com/2012/07/opening-closed-ports-on-nat-device-and.html).

## Admin UI

### Network Map

The Network Map, available under the `Network -> Map` tab in Admin UI, presents a dynamic map of the zombie browser's local network(s). Identified network hosts are added to the map automatically.

![Network Map of a zombie browser's local network](https://cloud.githubusercontent.com/assets/434827/10267111/0117cf3a-6ad2-11e5-9b39-cb747f06a13c.png)

The Network Map makes use of HTML5 canvas which allows you to save the map as an image.

![Save Network Map canvas as image](https://cloud.githubusercontent.com/assets/434827/10267112/06171dc4-6ad2-11e5-9e3d-7da364f3285e.png)

### Network Hosts

Right-clicking anywhere in the `Network -> Hosts` grid provides a context menu which provides options for host discovery.

![host-discovery](https://cloud.githubusercontent.com/assets/434827/6025988/e49e6dca-ac2a-11e4-909a-18c1de74ac27.png)

The first two menu items (for Chrome and Firefox) attempt to detect the local network IP address ranges:
* [Get Internal IP WebRTC](https://github.com/beefproject/beef/wiki/Module%3A-Get-Internal-IP-webrtc). (C, FF)
* Identify LAN subnets (C, FF)

The remaining options perform host discovery on a user-specified IP address range or a predefined list of commonly used LAN IP addresses:
* Discover Routers (S, FF)
* Discover Web Servers (ALL)
* Fingerprint HTTP (C, FF, IE, S)
* Cross-Origin CORS Scan (IE10+, C, FF, S)
* Cross-Origin Flash Scan (C, FF)


Identified network hosts are available in the `Network -> Hosts` panel.

Right-clicking a network host allows you to perform various actions on the host or all hosts in its local subnet, such as:
* Scan for HTTP servers (ALL)
* Fingerprint HTTP servers (C, FF, IE, S)
* Cross-Origin scan for CORS enabled HTTP servers (IE10+, C, FF, S)
* Cross-Origin scan for Flash cross-origin enabled HTTP servers (C, FF)
* Scan for open TCP ports (C, FF)

![service-discovery](https://cloud.githubusercontent.com/assets/434827/6026008/09b3323a-ac2b-11e4-90d5-2473208e5932.png)

### Network Services

Identified network services are available in the `Network -> Services` panel.

Right-clicking a network service allows you to perform various actions, such as:
* Fingerprint HTTP servers
* Cross-Origin scan host for CORS enabled HTTP servers
* Cross-Origin scan host for Flash cross-origin enabled HTTP servers
* Scan for remote file include (reverse shell)
* Scan for known vulnerable Shell Shock CGIs. (reverse shell)

![service-scanning](https://cloud.githubusercontent.com/assets/434827/6026013/14d547a2-ac2b-11e4-9cd3-9ce7ad51e7d4.png)


## RESTful API

The Network Extension RESTful API allows retrieval of the identified network hosts and services.
```
 # Returns the entire list of network hosts for all zombies
curl http://127.0.0.1:3000/api/network/hosts?token=[token]

# Returns the entire list of network services for all zombies
curl http://127.0.0.1:3000/api/network/services?token=[token]

# Returns all hosts given a specific hooked browser id
curl http://127.0.0.1:3000/api/network/hosts/[id]?token=[token]

# Returns all services given a specific hooked browser id
curl http://127.0.0.1:3000/api/network/services/[id]?token=[token]

# Returns a specific network host given its id
curl http://127.0.0.1:3000/api/network/host/[id]?token=[token]

# Returns a specific network service given its id
curl http://127.0.0.1:3000/api/network/service/[id]?token=[token]
```


***
[[Previous|Social-Engineering]] | [[Next|Metasploit]]