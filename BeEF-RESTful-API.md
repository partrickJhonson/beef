## Introduction
From version 0.4.3.3 BeEF exposes a RESTful API. All the exchanged data uses the JSON format, for both HTTP responses and HTTP POST requests that have a body. In order to use the API, a _token_ parameter must be always added to requests, otherwise a 401 error (Not Authorized) is returned.

The pseudo-random token is newly generated every time BeEF starts, using `BeEF::Core::Crypto::api_token` 
and is then added to the _BeEF::Configuration_ object. It can be retrieved at any time via ruby using `BeEF::Core::Configuration.instance.get('beef.api_token')`

When BeEF starts, look at the console output for 
`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`. That will be the value of the _token_ parameter
## Hooked Browsers
**Handler** => /api/hooks
## Logs
**Handler** => /api/logs
## Command Modules
**Handler** => /api/modules