JSDoc was used for documenting this API, you can run this locally for and find the output HTML in the beef/doc/rdoc folder.

* beef.are
* beef.browser
* beef.browser.cookie
* beef.browser.popup
* beef.dom
* beef.encode.base64
* beef.encode.json
* beef.geolocation
* beef.hardware
* beef.logger
* beef.mitb
* beef.net
* beef.net.connection
* beef.net.cors
* beef.net.dns
* beef.net.local
* beef.net.os
* beef.net.portscanner
* beef.net.requester
* beef.net.xssrays
* beef.session
* beef.updater
* beef.webrtc
* beef.websocket


***

**beef.are**

* status_success
* status_unknown
* status_error

**beef.browser**

* getBrowserReportedName
* isA
* isI
* isIE6
* isIE7
* isIE8
* isIE9
* isIE10
* isIE11
* isIE
* isFF2
* isFF3
* isFF3_5
* isFF3_6
* isFF4
* isFF5
* isFF6
* isFF7
* isFF8
* isFF9
* isFF10
* isFF11
* isFF12
* isFF13
* isFF14
* isFF15
* isFF16
* isFF17
* isFF18
* isFF19
* isFF20
* isFF21
* isFF22
* isFF23
* isFF24
* isFF25
* isFF26
* isFF27
* isFF28
* isFF29
* isFF30
* isFF31
* isFF32
* isFF33
* isFF34
* isFF35
* isFF36
* isFF37
* isFF38
* isFF39
* isFF40
* isFF41
* isFF
* isS4
* isS5
* isS6
* isS7
* isS8
* isS
* isC5
* isC6
* isC7
* isC8
* isC9
* isC10
* isC11
* isC12
* isC13
* isC14
* isC15
* isC16
* isC17
* isC18
* isC19
* isC19iOS
* isC20
* isC20iOS
* isC21
* isC21iOS
* isC22
* isC22iOS
* isC23
* isC23iOS
* isC24
* isC24iOS
* isC25
* isC25iOS
* isC26
* isC26iOS
* isC27
* isC27iOS
* isC28
* isC28iOS
* isC29
* isC29iOS
* isC30
* isC30iOS
* isC31
* isC31iOS
* isC32
* isC32iOS
* isC33
* isC33iOS
* isC34
* isC34iOS
* isC35
* isC35iOS
* isC36
* isC36iOS
* isC37
* isC37iOS
* isC38
* isC38iOS
* isC39
* isC39iOS
* isC40
* isC40iOS
* isC41
* isC41iOS
* isC42
* isC42iOS
* isC43
* isC43iOS
* isC44
* isC44iOS
* isC45
* isC46
* isC45iOS
* isC
* isO9_52
* isO9_60
* isO10
* isO11
* isO12
* isO
* capabilities
* type
* getBrowserVersion
* getBrowserName
* hookChildFrames
* hasFlash
* hasQuickTime
* hasRealPlayer
* hasWMP
* hasVLC
* javaEnabled
* hasPhonegap
* hasCors
* hasJava
* hasVBScript
* getPlugins
* getPluginsIE
* getScreenSize
* getWindowSize
* getDetails
* hasActiveX
* hasWebRTC
* hasSilverlight
* hasVisited: function (urls)
* hasWebSocket
* hasGoogleGears
* hasFoxit
* getPageHead
* getPageBody
* changeFavicon: function (favicon_url)
* changePageTitle: function (title)
* getBrowserLanguage
* getMaxConnections: function (scope)

**beef.browser.cookie**

* setCookie: function (name, value, expires, path, domain, secure) 
* getCookie: function(name) 
* deleteCookie: function (name, path, domain) 
* veganLol
* hasSessionCookies
* hasPersistentCookies

**beef.browser.popup**

* blocker_enabled

**beef.dom**

* generateID: function(prefix)
* createElement: function(type, attributes)
* removeElement: function(el)
* isDOMElement: function(obj)
* createInvisibleIframe
* getHighestZindex: function(include_id)
* createIframe: function(type, params, styles, onload)
* persistentIframe
* grayOut: function(vis, options)
* removeStylesheets
* createForm: function(params, append)
* getLocation
* getLinks
* rewriteLinks: function(url, selector)
* rewriteLinksClickEvents: function(url, selector)
* rewriteLinksProtocol: function(old_protocol, new_protocol, selector)
* rewriteTelLinks: function(new_number, selector)
* parseAppletParams: function(params)
* attachApplet: function(id, name, code, codebase, archive, params)
* detachApplet: function(id)
* createIframeXsrfForm: function(action, method, enctype, inputs)

**beef.encode.base64**

* keyStr
* encode: function (input)
* decode: function (input)
* utf8_encode: function (string)
* utf8_decode: function (utftext)

**beef.encode.json**

* stringify: function(o)
* quoteString: function(string)

**beef.geolocation**

* isGeolocationEnabled
* getOpenStreetMapAddress: function(command_url, command_id, latitude, longitude)
* getGeolocation: function (command_url, command_id)

**beef.hardware**

* ua
* cpuType
* isTouchEnabled
* isVirtualMachine
* isLaptop
* isNokia
* isZune
* isHtc
* isEricsson
* isMotorola
* isGoogle
* isMobilePhone
* getName

**beef.logger**

* running
* id
* running
* stream
* target
* time
* e
* start
* stop
* get_id
* click: function(e)
* win_focus: function(e)
* win_blur: function(e)
* keypress: function(e)
* copy: function(x)
* cut
* paste
* submit: function(e)
* push_stream
* get_dom_identifier: function(target)
* get_timestamp
* parse_stream
* queue

**beef.mitb**

* cid
* curl
* init: function (cid, curl)
* hook
* poisonAnchor: function (e)
* poisonForm: function (form)
* fetchForm: function (url, query, target)
* fetch: function (url, target)
* fetchOnclick: function (url)
* sniff: function (result)
* endSession

**beef.net**

* host
* port
* hook
* httpproto
* handler
* chop
* pad
* sid_count
* cmd_queue
* command
* packet
* stream
* response
* queue: function (handler, cid, results, status, callback)
* send: function (handler, cid, results, exec_status, callback)
* flush
* chunk: function (str, amount)
* push: function (stream)
* request: function (scheme, method, domain, port, path, anchor, data, timeout, dataType, callback)
* forge_request: function (scheme, method, domain, port, path, anchor, headers, data, timeout, dataType, allowCrossDomain, requestid, callback)
* clean: function (r)
* array_has_string_key: function (arr)
* browser_details


**beef.net.connection**

* type
* downlinkMax


**beef.net.cors**

* response
* request: function(method, url, data, callback)

**beef.net.dns**

* send: function(msgId, data, domain, callback)


**beef.net.local**

* sock
* checkJava
* hasJava
* initializeSocket
* getLocalAddress
* getLocalHostname

**beef.net.os**

* ua
* getDefaultBrowser
* isWin311
* isWinNT4
* isWin95
* isWinCE
* isWin98
* isWinME
* isWin2000
* isWin2000SP1
* isWinXP
* isWinServer2003
* isWinVista
* isWin7
* isWin8
* isWin81
* isOpenBSD
* isSunOS
* isLinux
* isMacintosh
* isOsxYosemite
* isOsxMavericks 
* isOsxSnowLeopard
* isOsxLeopard
* isWinPhone
* isIphone
* isIpad
* isIpod
* isNokia
* isAndroid
* isBlackBerry
* isWebOS
* isQNX
* isBeOS
* isWindows
* getName
* getVersion

**beef.net.portscanner**

* scanPort: function(callback, target, port, timeout)
* scanTarget: function(callback, target, ports_str, timeout)

**beef.net.requester**

* handler
* send: function(requests_array)

**beef.net.xssrays**

* handler
* completed
* totalConnections
* xssraysScanId
* hookedBrowserSession
* beefRayUrl
* crossDomain
* debug
* cleanUpTimeout
* vectors
* uniqueID
* rays
* stack
* checkBrowser: function(vector_array_index)
* printDebug: function(log)
* startScan: function(xssraysScanId, hookedBrowserSession, beefUrl, crossDomain, timeout, debug)
* complete
* getNextJob
* scan
* scanPaths
* scanForms
* scanLinks
* xss: function(target)
* host: function(url)
* fileName: function(url)
* urlEncode: function(str)
* run: function(url, method, vector, params, urlencode)
* runJobs
* timestamp
* escape: function(str)

**beef.session**

* hook_session_id_length
* hook_session_id_chars
* ec
* beefhook
* get_hook_session_id
* set_hook_session_id: function(id)
* gen_hook_session_id

**beef.updater**

* xhr_poll_timeout
* beefhook
* lock
* objects
* regObject: function(key, value)
* check
* get_commands
* execute_commands

**beef.webrtc**

TODO

**beef.websocket**

* socket
* ws_poll_timeout
* init
* start
* send: function (data)
* alive

***
[[Core BeEF Organization|Core BeEF Organization]] | [[Advanced Module Creation|Advanced Module Creation]]
