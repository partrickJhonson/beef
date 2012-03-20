## Introduction
From version 0.4.3.3 BeEF exposes a RESTful API. All the exchanged data uses the JSON format, for both HTTP responses and HTTP POST requests that have a body. In order to use the API, a _token_ parameter must be always added to requests, otherwise a 401 error (Not Authorized) is returned.

The pseudo-random token is newly generated every time BeEF starts, using `BeEF::Core::Crypto::api_token` 
and is then added to the _BeEF::Configuration_ object. It can be retrieved at any time via ruby using `BeEF::Core::Configuration.instance.get('beef.api_token')`

When BeEF starts, look at the console output for 
`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`. That will be the value of the _token_ parameter
## Hooked Browsers
**Handler** => /api/hooks
The _hooks_ handler gives information about the hooked browsers, both online and offline.

**Request**
`curl http://beefserver.com:3000/api/hooks?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response**

```text
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
## Logs
**Handler** => /api/logs
The _logs_ handler gives information about hooked browser logs, both global and relative ones.

**Request**
`curl http://beefserver.com:3000/api/logs?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```text
{
    "logs_count": 8,
    "logs": [
        {
            "id": 1,
            "date": "2012-03-20T16:14:11+01:00",
            "event": "127.0.0.1 just joined the horde from the domain: 127.0.0.1:3000",
            "type": "Zombie"
        },
<snip>
        {
            "id": 8,
            "date": "2012-03-20T16:18:27+01:00",
            "event": "19.092s - [Focus] Browser has regained focus.",
            "type": "Event"
        }
    ]
}
```

In order to retrieve relative hooked browser logs, so events that are logged for a specific browser, we must specify the unique session id that identified the browser in the BeEF framework. This information can be found from the previous /api/hooks call: the _session_ key value.

**Request**
`curl http://beefserver.com:3000/api/logs/nBK3BGBILYD0bNMC1IH299oDbZXNNXKfwMEoDwajmItAHhhhe8LLnEPvO3wFjg1rO4PzXsBbUAK1V0gk?token=320f3cf4da7bf0df7566a517c5db796e73a23f47`

**Response (snip)**

```text
{
    "logs_count": 13,
    "logs": [
        {
            "id": 1,
            "date": "2012-03-20T16:14:11+01:00",
            "event": "127.0.0.1 just joined the horde from the domain: 127.0.0.1:3000",
            "type": "Zombie"
        },
<snip>
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
<snip>
    ]
}
```
## Command Modules
**Handler** => /api/modules