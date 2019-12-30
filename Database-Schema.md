_Details of the database schema_

### Introduction ###

Database Schema

### ActiveRecord Tables ###

```
autoloader                         rules
commands                           dns_rule             
executions                         http         
mass_mailer                        interceptors       
browser_details                    web_cloner         
command_modules                    rtc_manage       
hooked_browsers                    rtc_signal
ipec_exploit                       rtc_status
ipec_exploit_run                   rtc_module_status
logs                               xssrays_details        
option_caches                      xssrays_scans          
network_service                    network_host                     
results                              
```

**HookedBrowser**

Stores hooked browser

```ruby
  storage_names[:default] = 'core_hookedbrowsers'
  property :id, Serial
  property :session, Text, :lazy => false
  property :ip, Text, :lazy => false
  property :firstseen, String, :length => 15
  property :lastseen, String, :length => 15
  property :httpheaders, Text, :lazy => false
  # @note the domain originating the hook request
  property :domain, Text, :lazy => false
  property :port, Integer, :default => 80
  property :count, Integer, :lazy => false
  property :has_init, Boolean, :default => false
  property :is_proxy, Boolean, :default => false
  # @note if true the HB is used as a tunneling proxy
```

**Command**

```ruby
  storage_names[:default] = 'commands'
  property :id, Serial
  property :data, Text
  property :creationdate, String, :length => 15, :lazy => false
  property :label, Text, :lazy => false
  property :instructions_sent, Boolean, :default => false
```

**CommandModule**

```ruby
  storage_names[:default] = 'core_commandmodules'
  property :id, Serial
  property :name, Text, :lazy => false
  property :path, Text, :lazy => false
```

**BrowserDetails**

```ruby
  storage_names[:default] = 'core_browserdetails'
  property :session_id, String, :length => 255, :key => true
  property :detail_key, String, :length => 255, :lazy => false, :key => true
  property :detail_value, Text, :lazy => false
```

**Log**

```ruby
  storage_names[:default] = 'core_logs'
  property :id, Serial
  property :type, Text, :lazy => false
  property :event, Text, :lazy => false
  property :date, DateTime, :lazy => false
  property :hooked_browser_id, Text, :lazy => false
```

**OptionCache**

```ruby
  storage_names[:default] = 'core_optioncache'
  property :id, Serial
  property :name, Text
  property :value, Text
```

**Result**

```ruby
  storage_names[:default] = 'core_results'
  property :id, Serial
  property :date, String, :length => 15, :lazy => false
  property :status, Integer
  property :data, Text
```

**User**

```ruby
  storage_names[:default] = 'extension_adminui_users'
  property :id, Serial
  property :session_id, String, :length => 255
  property :ip, Text
```

**NetworkHost**

```ruby
  storage_names[:default] = 'network_host'
  property :id, Serial
  property :hooked_browser_id, Text, :lazy => false
  property :ip, Text, :lazy => false
  property :hostname, String, :lazy => false
  property :type, String, :lazy => false # proxy, router, gateway, dns, etc
  property :os, String, :lazy => false
  property :mac, String, :lazy => false
  property :lastseen, String, :length => 15
```

**NetworkService**

```ruby
  storage_names[:default] = 'network_service'
  property :id, Serial
  property :hooked_browser_id, Text, :lazy => false
  property :proto, String, :lazy => false
  property :ip, Text, :lazy => false
  property :port, String, :lazy => false
  property :type, String, :lazy => false
```