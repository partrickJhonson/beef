## Introduction

Tunneling Proxy (TP) effectively mimics a reverse HTTP proxy. It will process requests via a selected browser session. This session becomes the tunnel and its [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] the exit point. 

#### Table of Contents

* [Details](#details)
* [Communication Flow](#communication-flow)
* [Real Scenarios](#real-scenarios)
* [How To Use The Proxy Extension](#how-to-use-the-proxy-extension)

## Details

A browser (or generally any software that supports a HTTP proxy) with its proxy configured to use BeEF will send all requests via the TP. 

The TP will create a set of instructions based on the received request details. These instructions will induce an equivalent request in whichever browser executes them. 

The instructions will be wrapped and sent to the selected browser session for execution on the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]]. The browser becomes the exit node for the tunnel. It will perform the request and receive the HTTP response.

The HTTP response is then communicated back to the BeEF proxy which delivers it to the browser. This process creates a tunnel with one being the TP and the other being the selected [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]].

The requests are not cross-origin: this means that if the current origin of the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] is `http://example.com:80`, the browser using the proxy can send requests only to `http://example.com:80`.

There are future plans to extend the tunneling proxy capabilities integrating Erlend Oftedal's [[malaRIA|http://erlend.oftedal.no/blog/?blogid=107]]. This will allow the tunneling proxy to forward requests to every origin with a liberal cross-origin policy.

```<allow-access-from origin="*">```

## Communication Flow

Browser -> ([[TP|https://github.com/beefproject/beef/wiki/Tunneling-Proxy/]]-[[CS|https://code.google.com/p/beef/w/edit/CommunicationServer]]) -> [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] -> (In-origin) Web Server -> [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] -> ([[TP|https://github.com/beefproject/beef/wiki/Tunneling-Proxy/]]-[[CS|https://code.google.com/p/beef/w/edit/CommunicationServer]]) -> Browser

## Real Scenarios

There are numerous real world use cases for the BeEF TP:
 * Browsing the authenticated surface of the hooked origin through the security context of the victim browser (cookies are automatically added to XmlHttpRequests with jQuery)
 * Spidering the hooked origin through the security context of the victim browser
 * Finding and exploiting SQLi with [[Burp Pro Scanner|http://portswigger.net/suite/pro.html]] and [[sqlmap|http://sqlmap.sourceforge.net/]].

A practical use of the TP, recorded as a screencast, can be found [[here|http://www.youtube.com/user/TheBeefproject#p/a/u/1/Z4cHyC3lowk]] on the official BeEF Youtube channel.

## How to Use the Proxy Extension

1. Select which [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] you want to use to tunnel requests. Right click on the hooked browser icon, then left click on "Use As Proxy".

[[Images/tunnel1.png|align=center]]

2. Configure another browser to use the TP as a HTTP proxy. 

<p align=center>
[[Images/tunnel2.png|align=center]]
</p>

3. In this case we had Opera (on the right of the screenshot) as the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]] and Firefox (on the left of the screenshot) as the browser using the TP. You can see that in Firefox we're simultaneously browsing the same origin of the Opera hooked browser (without stealing any cookies).

[[Images/tunnel3.png|align=center]]

4. Every request sent through the TP is using the Requester extension to send new XHRs to the [[hooked browser|https://github.com/beefproject/beef/wiki/Hooked-Browser]]. All of the raw request/response pairs are stored in the BeEF database and can be analyzed in detail via the Requester -> History tab.


[[Images/tunnel4.png|align=center]]

***

[[Previous|Metasploit]] | [[Next|Xss-Rays]]
