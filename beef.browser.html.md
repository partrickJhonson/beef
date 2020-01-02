<div id="main">

# Namespace: browser

<section>

<header>

## browser

</header>

<article>

<div class="container-overview">

<div class="description">

Basic browser functions.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 7](browser.js.html#line7)

</dd>

</dl>

</div>

### Namespaces

<dl>

<dt>[cookie](beef.browser.cookie.html)</dt>

<dt>[popup](beef.browser.popup.html)</dt>

</dl>

### Methods

#### <span class="type-signature">(static)</span> changeFavicon<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Dynamically changes the favicon: works in Firefox, Chrome and Opera

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4540](browser.js.html#line4540)

</dd>

</dl>

#### <span class="type-signature">(static)</span> changePageTitle<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Changes page title

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4561](browser.js.html#line4561)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getBrowserEngine<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the underlying layout engine in use by the browser.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 25](browser.js.html#line25)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getBrowserLanguage<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Get the browser language

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4568](browser.js.html#line4568)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getBrowserName<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the type of user agent by hooked browser.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3620](browser.js.html#line3620)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getBrowserReportedName<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the user agent that the browser is claiming to be.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 17](browser.js.html#line17)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getBrowserVersion<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the major version of the browser being used.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2730](browser.js.html#line2730)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getDetails<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Construct hash from browser details. This function is used to grab the browser details during the hooking process

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4183](browser.js.html#line4183)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getMaxConnections<span class="signature">()</span> <span class="type-signature">→ {Object}</span>

<div class="description">

A function that gets the max number of simultaneous connections the browser can make per origin, or globally on all origin.

This code is based on research from browserspy.dk

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4590](browser.js.html#line4590)

</dd>

</dl>

##### Returns:

<div class="param-desc">

A jQuery deferred object promise, which when resolved passes the number of connections to the callback function as "this"

</div>

<dl>

<dt>Type</dt>

<dd><span class="param-type">Object</span></dd>

</dl>

#### <span class="type-signature">(static)</span> getPageBody<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the page body HTML

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4528](browser.js.html#line4528)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getPageHead<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the page head HTML

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4516](browser.js.html#line4516)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getPlugins<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the list of plugins installed in the browser.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3916](browser.js.html#line3916)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getPluginsIE<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns a list of plugins detected by IE. This is a hack because IE doesn't support navigator.plugins

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4084](browser.js.html#line4084)

</dd>

</dl>

#### <span class="type-signature">(static)</span> getWindowSize<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns zombie browser window size.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4159](browser.js.html#line4159)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasActiveX<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns boolean value depending on whether the browser supports ActiveX

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4349](browser.js.html#line4349)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasCors<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the browser supports CORS

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3876](browser.js.html#line3876)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasFlash<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has flash installed and enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3698](browser.js.html#line3698)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasFoxit<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Foxit PDF reader plugin.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4495](browser.js.html#line4495)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasGoogleGears<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Google Gears installed.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4454](browser.js.html#line4454)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasJava<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Java installed and enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3891](browser.js.html#line3891)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasPhonegap<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the Phonegap API is available from the hooked origin.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3858](browser.js.html#line3858)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasQuickTime<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has the QuickTime plugin installed.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3731](browser.js.html#line3731)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasRealPlayer<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has the RealPlayer plugin installed.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3759](browser.js.html#line3759)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasSilverlight<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns boolean value depending on whether the browser supports Silverlight

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4363](browser.js.html#line4363)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasVBScript<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has VBScript enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3905](browser.js.html#line3905)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasVisited<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns array of results, whether or not the target zombie has visited the specified URL

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4383](browser.js.html#line4383)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasVLC<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if VLC is installed

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3824](browser.js.html#line3824)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasWebGL<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has WebGL enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4438](browser.js.html#line4438)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasWebRTC<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns boolean value depending on whether the browser supports WebRTC

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4356](browser.js.html#line4356)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasWebSocket<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Web Sockets enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4420](browser.js.html#line4420)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasWebWorker<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Web Workers enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 4428](browser.js.html#line4428)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hasWMP<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has the Windows Media Player plugin installed.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3798](browser.js.html#line3798)

</dd>

</dl>

#### <span class="type-signature">(static)</span> hookChildFrames<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Hooks all child frames in the current window Restricted by same-origin policy

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3672](browser.js.html#line3672)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isA<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Avant Browser.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 38](browser.js.html#line38)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isBrave<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Brave

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 70](browser.js.html#line70)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2437](browser.js.html#line2437)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC5<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 5.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1029](browser.js.html#line1029)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC6<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 6.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1037](browser.js.html#line1037)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC7<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 7.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1045](browser.js.html#line1045)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC8<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 8.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1053](browser.js.html#line1053)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC9<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 9.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1061](browser.js.html#line1061)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC10<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 10.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1069](browser.js.html#line1069)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC11<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 11.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1077](browser.js.html#line1077)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC12<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 12.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1085](browser.js.html#line1085)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC13<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 13.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1093](browser.js.html#line1093)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC14<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 14.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1101](browser.js.html#line1101)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC15<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 15.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1109](browser.js.html#line1109)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC16<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 16.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1117](browser.js.html#line1117)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC17<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 17.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1125](browser.js.html#line1125)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC18<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 18.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1133](browser.js.html#line1133)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC19<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 19.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1141](browser.js.html#line1141)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC19iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 19.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1149](browser.js.html#line1149)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC20<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 20.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1157](browser.js.html#line1157)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC20iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 20.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1165](browser.js.html#line1165)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC21<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 21.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1173](browser.js.html#line1173)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC21iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 21.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1181](browser.js.html#line1181)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC22<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 22.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1189](browser.js.html#line1189)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC22iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 22.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1197](browser.js.html#line1197)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC23<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 23.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1205](browser.js.html#line1205)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC23iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 23.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1213](browser.js.html#line1213)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC24<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 24.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1221](browser.js.html#line1221)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC24iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 24.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1229](browser.js.html#line1229)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC25<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 25.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1237](browser.js.html#line1237)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC25iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 25.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1245](browser.js.html#line1245)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC26<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 26.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1253](browser.js.html#line1253)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC26iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 26.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1261](browser.js.html#line1261)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC27<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 27.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1269](browser.js.html#line1269)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC27iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 27.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1277](browser.js.html#line1277)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC28<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 28.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1285](browser.js.html#line1285)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC28iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 28.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1293](browser.js.html#line1293)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC29<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 29.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1301](browser.js.html#line1301)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC29iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 29.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1309](browser.js.html#line1309)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC30<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 30.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1317](browser.js.html#line1317)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC30iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 30.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1325](browser.js.html#line1325)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC31<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 31.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1333](browser.js.html#line1333)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC31iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 31.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1341](browser.js.html#line1341)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC32<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 32.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1349](browser.js.html#line1349)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC32iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 32.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1357](browser.js.html#line1357)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC33<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 33.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1365](browser.js.html#line1365)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC33iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 33.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1373](browser.js.html#line1373)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC34<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 34.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1381](browser.js.html#line1381)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC34iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 34.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1389](browser.js.html#line1389)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC35<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 35.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1397](browser.js.html#line1397)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC35iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 35.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1405](browser.js.html#line1405)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC36<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 36.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1413](browser.js.html#line1413)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC36iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 36.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1421](browser.js.html#line1421)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC37<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 37.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1429](browser.js.html#line1429)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC37iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 37.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1437](browser.js.html#line1437)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC38<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 38.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1445](browser.js.html#line1445)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC38iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 38.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1453](browser.js.html#line1453)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC39<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 39.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1461](browser.js.html#line1461)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC39iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 39.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1469](browser.js.html#line1469)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC40<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 40.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1477](browser.js.html#line1477)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC40iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 40.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1485](browser.js.html#line1485)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC41<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 41.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1493](browser.js.html#line1493)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC41iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 41.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1501](browser.js.html#line1501)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC42<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 42.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1509](browser.js.html#line1509)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC42iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 42.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1517](browser.js.html#line1517)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC43<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 43.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1525](browser.js.html#line1525)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC43iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 43.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1533](browser.js.html#line1533)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC44<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 44.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1541](browser.js.html#line1541)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC44iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 44.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1549](browser.js.html#line1549)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC45<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 45.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1557](browser.js.html#line1557)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC45iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 45.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1565](browser.js.html#line1565)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC46<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 46.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1573](browser.js.html#line1573)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC46iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 46.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1581](browser.js.html#line1581)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC47<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 47.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1589](browser.js.html#line1589)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC47iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 47.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1597](browser.js.html#line1597)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC48<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 48.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1605](browser.js.html#line1605)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC48iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 48.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1613](browser.js.html#line1613)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC49<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 49.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1621](browser.js.html#line1621)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC49iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 49.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1629](browser.js.html#line1629)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC50<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 50.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1637](browser.js.html#line1637)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC50iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 50.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1645](browser.js.html#line1645)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC51<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 51.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1653](browser.js.html#line1653)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC51iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 51.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1661](browser.js.html#line1661)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC52<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 52.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1669](browser.js.html#line1669)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC52iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 52.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1677](browser.js.html#line1677)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC53<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 53.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1685](browser.js.html#line1685)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC53iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 53.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1693](browser.js.html#line1693)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC54<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 54.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1701](browser.js.html#line1701)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC54iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 54.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1709](browser.js.html#line1709)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC55<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 55.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1717](browser.js.html#line1717)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC55iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 55.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1725](browser.js.html#line1725)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC56<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 56.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1733](browser.js.html#line1733)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC56iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 56.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1741](browser.js.html#line1741)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC57<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 57.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1749](browser.js.html#line1749)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC57iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 57.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1757](browser.js.html#line1757)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC58<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 58.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1765](browser.js.html#line1765)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC58iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 58.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1773](browser.js.html#line1773)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC59<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 59.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1781](browser.js.html#line1781)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC59iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 59.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1789](browser.js.html#line1789)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC60<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 60.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1797](browser.js.html#line1797)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC60iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 60.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1805](browser.js.html#line1805)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC61<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 61.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1813](browser.js.html#line1813)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC61iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 61.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1821](browser.js.html#line1821)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC62<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 62.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1829](browser.js.html#line1829)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC62iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 62.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1837](browser.js.html#line1837)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC63<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 63.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1845](browser.js.html#line1845)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC63iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 63.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1853](browser.js.html#line1853)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC64<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 64.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1861](browser.js.html#line1861)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC64iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 64.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1869](browser.js.html#line1869)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC65<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 65.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1877](browser.js.html#line1877)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC65iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 65.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1885](browser.js.html#line1885)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC66<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 66.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1893](browser.js.html#line1893)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC66iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 66.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1901](browser.js.html#line1901)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC67<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 67.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1909](browser.js.html#line1909)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC67iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 67.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1917](browser.js.html#line1917)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC68<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 68.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1925](browser.js.html#line1925)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC68iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 68.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1933](browser.js.html#line1933)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC69<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 69.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1941](browser.js.html#line1941)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC69iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 69.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1949](browser.js.html#line1949)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC70<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 70.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1957](browser.js.html#line1957)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC70iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 70.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1965](browser.js.html#line1965)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC71<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 71.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1973](browser.js.html#line1973)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC71iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 71.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1981](browser.js.html#line1981)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC72<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 72.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1989](browser.js.html#line1989)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC72iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 72.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1997](browser.js.html#line1997)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC73<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 73.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2005](browser.js.html#line2005)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC73iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 73.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2013](browser.js.html#line2013)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC74<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 74.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2021](browser.js.html#line2021)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC74iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 74.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2029](browser.js.html#line2029)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC75<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 75.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2037](browser.js.html#line2037)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC75iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 75.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2045](browser.js.html#line2045)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC76<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 76.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2053](browser.js.html#line2053)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC76iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 76.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2061](browser.js.html#line2061)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC77<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 77.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2069](browser.js.html#line2069)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC77iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 77.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2077](browser.js.html#line2077)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC78<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 78.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2085](browser.js.html#line2085)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC78iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 78.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2093](browser.js.html#line2093)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC79<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 79.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2101](browser.js.html#line2101)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC79iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 79.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2109](browser.js.html#line2109)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC80<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 80.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2117](browser.js.html#line2117)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC80iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 80.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2125](browser.js.html#line2125)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC81<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 81.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2133](browser.js.html#line2133)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC81iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 81.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2141](browser.js.html#line2141)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC82<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 82.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2149](browser.js.html#line2149)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC82iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 82.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2157](browser.js.html#line2157)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC83<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 83.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2165](browser.js.html#line2165)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC83iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 83.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2173](browser.js.html#line2173)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC84<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 84.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2181](browser.js.html#line2181)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC84iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 84.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2189](browser.js.html#line2189)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC85<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 85.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2197](browser.js.html#line2197)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC85iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 85.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2205](browser.js.html#line2205)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC86<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 86.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2213](browser.js.html#line2213)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC86iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 86.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2221](browser.js.html#line2221)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC87<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 87.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2229](browser.js.html#line2229)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC87iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 87.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2237](browser.js.html#line2237)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC88<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 88.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2245](browser.js.html#line2245)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC88iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 88.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2253](browser.js.html#line2253)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC89<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 89.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2261](browser.js.html#line2261)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC89iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 89.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2269](browser.js.html#line2269)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC90<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 90.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2277](browser.js.html#line2277)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC90iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 90.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2285](browser.js.html#line2285)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC91<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 91.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2293](browser.js.html#line2293)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC91iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 91.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2301](browser.js.html#line2301)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC92<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 92.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2309](browser.js.html#line2309)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC92iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 92.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2317](browser.js.html#line2317)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC93<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 93.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2325](browser.js.html#line2325)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC93iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 93.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2333](browser.js.html#line2333)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC94<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 94.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2341](browser.js.html#line2341)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC94iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 94.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2349](browser.js.html#line2349)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC95<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 95.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2357](browser.js.html#line2357)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC95iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 95.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2365](browser.js.html#line2365)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC96<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 96.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2373](browser.js.html#line2373)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC96iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 96.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2381](browser.js.html#line2381)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC97<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 97.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2389](browser.js.html#line2389)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC97iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 97.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2397](browser.js.html#line2397)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC98<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 98.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2405](browser.js.html#line2405)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC98iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 98.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2413](browser.js.html#line2413)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC99<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome 99.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2421](browser.js.html#line2421)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isC99iOS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Chrome for iOS 99.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2429](browser.js.html#line2429)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isEdge<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Edge.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 129](browser.js.html#line129)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isEpi<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Return true if Epiphany

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1017](browser.js.html#line1017)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 945](browser.js.html#line945)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF2<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF2.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 145](browser.js.html#line145)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF3<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF3.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 153](browser.js.html#line153)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF3_5<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF3.5.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 161](browser.js.html#line161)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF3_6<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF3.6.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 169](browser.js.html#line169)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF4<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF4.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 177](browser.js.html#line177)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF5<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF5.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 185](browser.js.html#line185)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF6<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF6.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 193](browser.js.html#line193)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF7<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF7.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 201](browser.js.html#line201)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF8<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF8.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 209](browser.js.html#line209)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF9<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF9.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 217](browser.js.html#line217)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF10<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF10.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 225](browser.js.html#line225)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF11<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF11.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 233](browser.js.html#line233)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF12<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF12

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 241](browser.js.html#line241)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF13<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF13

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 249](browser.js.html#line249)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF14<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF14

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 257](browser.js.html#line257)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF15<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF15

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 265](browser.js.html#line265)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF16<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF16

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 273](browser.js.html#line273)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF17<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF17

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 281](browser.js.html#line281)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF18<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF18

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 289](browser.js.html#line289)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF19<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF19

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 297](browser.js.html#line297)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF20<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF20

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 305](browser.js.html#line305)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF21<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF21

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 313](browser.js.html#line313)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF22<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF22

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 321](browser.js.html#line321)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF23<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF23

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 329](browser.js.html#line329)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF24<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF24

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 337](browser.js.html#line337)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF25<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF25

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 345](browser.js.html#line345)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF26<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF26

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 353](browser.js.html#line353)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF27<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF27

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 361](browser.js.html#line361)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF28<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF28

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 369](browser.js.html#line369)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF29<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF29

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 377](browser.js.html#line377)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF30<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF30

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 385](browser.js.html#line385)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF31<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF31

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 393](browser.js.html#line393)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF32<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF32

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 401](browser.js.html#line401)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF33<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF33

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 409](browser.js.html#line409)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF34<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF34

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 417](browser.js.html#line417)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF35<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF35

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 425](browser.js.html#line425)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF36<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF36

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 433](browser.js.html#line433)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF37<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF37

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 441](browser.js.html#line441)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF38<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF38

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 449](browser.js.html#line449)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF39<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF39

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 457](browser.js.html#line457)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF40<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF40

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 465](browser.js.html#line465)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF41<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF41

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 473](browser.js.html#line473)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF42<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF42

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 481](browser.js.html#line481)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF43<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF43

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 489](browser.js.html#line489)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF44<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF44

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 497](browser.js.html#line497)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF45<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF45

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 505](browser.js.html#line505)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF46<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF46

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 513](browser.js.html#line513)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF47<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF47

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 521](browser.js.html#line521)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF48<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF48

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 529](browser.js.html#line529)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF49<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF49

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 537](browser.js.html#line537)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF50<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF50

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 545](browser.js.html#line545)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF51<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF51

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 553](browser.js.html#line553)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF52<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF52

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 561](browser.js.html#line561)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF53<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF53

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 569](browser.js.html#line569)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF54<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF54

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 577](browser.js.html#line577)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF55<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF55

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 585](browser.js.html#line585)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF56<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF56

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 593](browser.js.html#line593)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF57<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF57

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 601](browser.js.html#line601)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF58<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF58

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 609](browser.js.html#line609)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF59<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF59

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 617](browser.js.html#line617)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF60<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF60

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 625](browser.js.html#line625)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF61<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF61

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 633](browser.js.html#line633)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF62<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF62

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 641](browser.js.html#line641)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF63<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF63

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 649](browser.js.html#line649)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF64<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF64

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 657](browser.js.html#line657)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF65<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF65

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 665](browser.js.html#line665)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF66<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF66

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 673](browser.js.html#line673)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF67<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF67

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 681](browser.js.html#line681)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF68<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF68

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 689](browser.js.html#line689)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF69<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF69

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 697](browser.js.html#line697)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF70<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF70

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 705](browser.js.html#line705)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF71<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF71

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 713](browser.js.html#line713)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF72<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF72

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 721](browser.js.html#line721)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF73<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF73

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 729](browser.js.html#line729)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF74<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF74

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 737](browser.js.html#line737)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF75<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF75

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 745](browser.js.html#line745)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF76<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF76

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 753](browser.js.html#line753)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF77<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF77

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 761](browser.js.html#line761)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF78<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF78

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 769](browser.js.html#line769)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF79<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF79

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 777](browser.js.html#line777)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF80<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF80

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 785](browser.js.html#line785)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF81<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF81

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 793](browser.js.html#line793)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF82<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF82

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 801](browser.js.html#line801)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF83<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF83

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 809](browser.js.html#line809)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF84<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF84

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 817](browser.js.html#line817)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF85<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF85

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 825](browser.js.html#line825)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF86<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF86

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 833](browser.js.html#line833)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF87<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF87

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 841](browser.js.html#line841)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF88<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF88

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 849](browser.js.html#line849)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF89<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF89

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 857](browser.js.html#line857)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF90<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF90

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 865](browser.js.html#line865)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF91<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF91

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 873](browser.js.html#line873)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF92<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF92

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 881](browser.js.html#line881)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF93<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF93

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 889](browser.js.html#line889)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF94<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF94

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 897](browser.js.html#line897)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF95<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF95

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 905](browser.js.html#line905)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF96<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF96

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 913](browser.js.html#line913)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF97<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF97

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 921](browser.js.html#line921)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF98<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF98

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 929](browser.js.html#line929)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isFF99<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if FF99

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 937](browser.js.html#line937)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIceweasel<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Iceweasel.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 46](browser.js.html#line46)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 137](browser.js.html#line137)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE6<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE6.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 78](browser.js.html#line78)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE7<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE7.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 86](browser.js.html#line86)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE8<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE8.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 94](browser.js.html#line94)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE9<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE9.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 102](browser.js.html#line102)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE10<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE10.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 111](browser.js.html#line111)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isIE11<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if IE11.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 120](browser.js.html#line120)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isMidori<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Midori.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 54](browser.js.html#line54)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2485](browser.js.html#line2485)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO9_52<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera 9.50 through 9.52.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2445](browser.js.html#line2445)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO9_60<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera 9.60 through 9.64.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2453](browser.js.html#line2453)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO10<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera 10.xx.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2461](browser.js.html#line2461)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO11<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera 11.xx.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2469](browser.js.html#line2469)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isO12<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Opera 12.xx.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2477](browser.js.html#line2477)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isOdyssey<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Odyssey

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 62](browser.js.html#line62)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 993](browser.js.html#line993)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS4<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari 4.xx

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 953](browser.js.html#line953)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS5<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari 5.xx

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 961](browser.js.html#line961)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS6<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari 6.xx

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 969](browser.js.html#line969)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS7<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari 7.xx

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 977](browser.js.html#line977)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isS8<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Safari 8.xx

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 985](browser.js.html#line985)

</dd>

</dl>

#### <span class="type-signature">(static)</span> isWebKitBased<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns true if Webkit based

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 1002](browser.js.html#line1002)

</dd>

</dl>

#### <span class="type-signature">(static)</span> javaEnabled<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Checks if the zombie has Java enabled.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 3848](browser.js.html#line3848)

</dd>

</dl>

#### <span class="type-signature">(static)</span> type<span class="signature">()</span><span class="type-signature"></span>

<div class="description">

Returns the type of browser being used.

</div>

<dl class="details">

<dt class="tag-source">Source:</dt>

<dd class="tag-source">

*   [browser.js](browser.js.html), [line 2495](browser.js.html#line2495)

</dd>

</dl>

</article>

</section>

</div>

<nav>

## [Home](index.html)

### Namespaces

*   [are](beef.are.html)
*   [browser](beef.browser.html)
*   [cookie](beef.browser.cookie.html)
*   [popup](beef.browser.popup.html)
*   [dom](beef.dom.html)
*   [base64](beef.encode.base64.html)
*   [json](beef.encode.json.html)
*   [geolocation](beef.geolocation.html)
*   [hardware](beef.hardware.html)
*   [init](beef.init.html)
*   [logger](beef.logger.html)
*   [mitb](beef.mitb.html)
*   [net](beef.net.html)
*   [connection](beef.net.connection.html)
*   [cors](beef.net.cors.html)
*   [dns](beef.net.dns.html)
*   [local](beef.net.local.html)
*   [portscanner](beef.net.portscanner.html)
*   [requester](beef.net.requester.html)
*   [xssrays](beef.net.xssrays.html)
*   [os](beef.os.html)
*   [session](beef.session.html)
*   [timeout](beef.timeout.html)
*   [updater](beef.updater.html)
*   [webrtc](beef.webrtc.html)
*   [websocket](beef.websocket.html)
*   [BeefJS](BeefJS.html)
*   [browser_jools](browser_jools.html)
*   [platform](platform.html)

</nav>

<footer>Documentation generated by [JSDoc 3.6.3](https://github.com/jsdoc/jsdoc) on Thu Jan 02 2020 15:55:36 GMT+1000 (Australian Eastern Standard Time)</footer>

<script>prettyPrint();</script>