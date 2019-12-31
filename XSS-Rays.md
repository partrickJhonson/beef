## Introduction
XSS Rays is a pure Javascript Cross-Site Scripting ([XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))) scanner, orginally [developed by Gareth Heyes](http://www.thespanner.co.uk/2009/03/25/xss-ray) in 2009. XSS Rays parses all the links and forms of the page where it has been loaded and checks for XSS on the GET, POST parameters, and the URI path by creating hidden iFrames.

#### Table of Contents

* [Details](#details)
* [High Level Overview](#high-level-overview)
* [How to Use Xssrays Extension](#how-to-use-the-xssrays-extension)
* [What's Next?](#whats-next)

## Details
The original code by Heyes, from 2009, used the location.hash fragment in order to effectively have a callback between parent and child iFrames. This trick has been patched by recent browsers. BeEF uses a new approach which results in false-positive free findings. The reason they are false-positive free is that BeEF must exploit the XSS to discover the vulnerability. 

## High Level Overview
In order to check for XSS cross-origin, we inject an XSS payload that will contact the BeEF server if the Javascript code is successfully executed (thus, the XSS confirmed). In order to check for XSS on cross-origin resources, the approach is completely blind (because we cannot read the HTTP response, respecting the Same Origin Policy). The approach BeEF is using is not free of false-negatives, because we can try a different attack vectors but the framework cannot determine which characters are allowed or if there are any length limitations in place. This issue can be minimised by adding more attack vectors that covers different scenarios.


[[Images/xssrays1.png|align=center]]

## How to Use the Xssrays Extension
**1.** Select which [hooked browser](https://github.com/beefproject/beef/wiki/Hooked-Browser) to use to inject the Xssrays Javascript code. By default Xssrays will check for XSS on cross-origin resources. Note that the hooked browser origin is currently http://172.31.229.247/

![xssrays-how-to-use](http://antisnatchor.com/BeEF-images/XSSRAYS-select.png)
If you want to start a custom Xssrays scan, you can first configure the extension settings and then click on Scan. Here you can configure the default timeout for iFrames removal, and if cross-origin resources should be checked as well.

[[Images/xssrays3.png|align=center]]

**2.** When an XSS vulnerability is found, you will see a notification in the BeEF logs, something like "received ray from HB". Also, opening the XssRays->Logs tab you can see the details of the XSS that has been found by XssRays.

[[Images/xssrays4.png|align=center]]


**3.** If you have direct access to the application, you can test the Xssrays finding using the PoC provided. As you can see in the image below, the XSS that has been found by Xssrays was not a false-positive.

[[Images/xssrays5.png|align=center]]

## What's Next?
If Xssrays has found an XSS on a cross-origin resource, and you don't have access to that resource (i.e. a victim's internal network web server), the user could always trigger the victim to open a link that points to the vulnerable resource using the BeEF hook in your attack vector. In this way your attack surface will be expanded, and the same victim browser will be hooked in BeEF on 2 different origin: the original one, and the new one with the XSS found by XssRays.

***

[[Previous|Tunneling]] | [[Next|Persistence]]
