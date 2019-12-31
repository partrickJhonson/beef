
## Introduction
_Tunneling Proxy will process requests via a selected browser session._

The Tunneling Proxy (TP) effectively mimics a reverse HTTP proxy. A selected browser session becomes the tunnel and its [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] the exit point. 

#### Table of Contents

* [Details](#details)
* [Communication Flow](#communication-flow)
* [Real Scenarios](#real-scenarios)
* [How To Use The Proxy Extension](#how-to-use-the-proxy-extension)

## Details

A browser (or generally any software that supports an HTTP proxy) with its proxy configured to use the framework will send all its requests via the TP. The TP will create a set of instructions based on the received request details. These instructions will induce a browser to conduct an equivalent request.  Next the instructions will be wrapped and sent to the selected browser session for execution on the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]]. The browser becomes the exit node for the tunnel. It will perform the request and receive the HTTP response. Next the response is communicated back to the BeEF proxy which in turn delivers it to the browser. This process creates a tunnel with one being the TP and the other being the selected [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]].

The requests are not cross-origin: this means that if the current origin of the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] is `http://example.com:80`, the browser using the proxy can send requests only to `http://example.com:80`.

There are future plans to extend the tunneling proxy capabilities integrating Erlend Oftedal's [[malaRIA|http://erlend.oftedal.no/blog/?blogid=107]]. This will allow the tunneling proxy to forward requests to every origin with a liberal cross-origin policy.

```<allow-access-from origin="*">```

## Communication Flow

Browser -> ([[TP|https://github.com/beefproject/beef/wiki/Tunneling-Proxy/]]-[[CS|https://code.google.com/p/beef/w/edit/CommunicationServer]]) -> [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] -> (In-origin) Web Server -> [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] -> ([[TP|https://github.com/beefproject/beef/wiki/Tunneling-Proxy/]]-[[CS|https://code.google.com/p/beef/w/edit/CommunicationServer]]) -> Browser

## Real Scenarios

Tunneling proxy real use cases are many:
 - browsing the authenticated surface of the hooked origin through the security context of the victim browser (cookies are automatically added to XmlHttpRequests with jQuery)

 - spidering the hooked origin through the security context of the victim browser

 - finding and exploiting SQLi with [[Burp Pro Scanner|http://portswigger.net/suite/pro.html]] and [[sqlmap|http://sqlmap.sourceforge.net/]].

A practical usage of the tunneling proxy, recorded as a screencast, can be found [[here|http://www.youtube.com/user/TheBeefproject#p/a/u/1/Z4cHyC3lowk]] on the official BeEF Youtube channel.

## How to Use the Proxy Extension

*1.* Select which [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] you want to use to tunnel requests (right click on the HB icon, then left click on "Use As Proxy")

[[Images/tunnel1.png|align=center]]

*2.* Configure another browser to use the BeEF tunneling proxy as HTTP proxy. By default the address of the proxy is 127.0.0.1:6789

<p align=center>
[[Images/tunnel2.png|align=center]]
</p>

*3.* In this case we had Opera (on the right of the screenshot) as [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] and Firefox (on the left of the screenshot) as the browser using the tunneling proxy. You can see that in Firefox we're browsing the same origin of the Opera hooked browser in a concurrent way (without stealing any cookies).  

[[Images/tunnel3.png|align=center]]

*4.* Every request sent through the Tunneling Proxy is using the Requester extension to send new XHRs to the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]]. All the raw request/response pairs are stored in the BeEF database and can be analyzed in detail via the Requester->History tab.


[[Images/tunnel4.png|align=center]]

***

[[Previous|Metasploit]] | [[Next|Xss-Rays]]
