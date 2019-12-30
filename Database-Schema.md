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

To view all fields within these tables please see the ActiveRecord::Migration
https://github.com/beefproject/beef/tree/master/core/main/ar-migrations