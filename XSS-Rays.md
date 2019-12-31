## Introduction

XSS Rays is a pure Javascript Cross-Site Scripting ([XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))) scanner, orginally [developed by Gareth Heyes](http://www.thespanner.co.uk/2009/03/25/xss-ray) in 2009.

XSS Rays parses all the links and forms of the page where it has been loaded and checks for XSS on the GET, POST parameters, and the URI path by creating hidden iFrames.

#### Table of Contents

* [Details](#details)
* [High Level Overview](#high-level-overview)
* [How to Use Xssrays Extension](#how-to-use-the-xssrays-extension)

## Details

The original code by Heyes used the location.hash fragment in order to effectively create a callback between parent and child iFrames. This trick has been patched by recent browsers. 

BeEF utilises a new approach to this technique which results in false-positive free findings. They are false-positive free because BeEF must exploit the XSS in order to discover the vulnerability. 

## High Level Overview

In order to check for XSS cross-origin, we inject an XSS payload that will contact the BeEF server if the Javascript code is successfully executed, thereby confirming XSS. In order to check for XSS on cross-origin resources, the approach is completely blind (because we cannot read the HTTP response, respecting the Same Origin Policy).

The approach BeEF is using is not free of false-negatives. We can try different attack vectors but the framework cannot determine which characters are allowed or if there are any length limitations in place. This issue can only be minimised by adding more attack vectors that covers a larger variety of scenarios.

#### BeEF XSS Rays Integration:

[[Images/xssrays1.png|align=center]]

## How to Use the XSS Rays Extension

1. Select which [hooked browser](https://github.com/beefproject/beef/wiki/Hooked-Browser) to inject the XSS Rays Javascript code into. By default XSS Rays will check for XSS on cross-origin resources. Note that the hooked browser origin is currently http://172.31.229.247/

![xssrays-how-to-use](http://antisnatchor.com/BeEF-images/XSSRAYS-select.png)  

  * Alternatively if you want to start your own custom XSS Rays scan, you can first configure the extension settings and then click on `Scan`. Here you can configure the default timeout for the iFrame's removal, and select whether cross-origin resources should be checked as well.  
  
[[Images/xssrays3.png|align=center]]

2. When a XSS vulnerability is found, you will see a notification in the BeEF logs. Opening the `XssRays -> Logs` tab will show you more details about the discovered XSS.

[[Images/xssrays4.png|align=center]]

3. If you have direct access to the application, you can test the XSS Rays finding using the PoC provided in the `Logs` tab shown in the previous step.

[[Images/xssrays5.png|align=center]]

### What If I Don't Have Direct Application Access?

If XSS Rays discovers an XSS vulnerability on a cross-origin resource, and you don't have access to that resource (i.e. a victim's internal network web server), you can always utilise a command module that will trigger the victim to open a link that is pointing to the vulnerable resource.

By doing this, your attack surface will be expanded, and the same victim browser will be hooked to BeEF on two different origins: the original hook, and the application hooked with the XSS found by XSS Rays.

***

[[Previous|Tunneling]] | [[Next|Persistence]]