## Introduction
From version 0.4.3.3 BeEF exposes a RESTful API. All the exchanged data uses the JSON format, for both HTTP responses and HTTP POST requests that have a body. In order to use the API, a _token_ parameter must be always added to requests, otherwise a 401 error (Not Authorized) is returned.

The pseudo-random token is newly generated every time BeEF starts, using _BeEF::Core::Crypto::api_token_ 
and is then added to the _BeEF::Configuration_ object. It can be retrieved at any time via ruby using _BeEF::Core::Configuration.instance.get('beef.api_token')_
## Hooked Browsers
**Handler** => /api/hooks
## Logs
**Handler** => /api/logs
## Command Modules
**Handler** => /api/modules