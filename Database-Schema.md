_Details of the database schema_

### Introduction ###

Database Schema

### Database Tables ###

```
sqlite> .tables
ar_internal_metadata  interceptors          rtc_manage          
autoloader            ipec_exploit          rtc_module_status   
browser_details       ipec_exploit_run      rtc_signal          
command_modules       logs                  rtc_status          
commands              mass_mailer           rules               
dns_rule              network_hosts         schema_migrations   
executions            network_services      web_cloner          
hooked_browsers       option_caches         xssrays_detail      
http                  results               xssrays_scan 
```

### Table Info ###

```
sqlite> PRAGMA table_info(ar_internal_metadata);
```
cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | key | varchar | 1 | | 1
1 | value | varchar | 0 | | 0
2 | created_at | datetime(6) | 1 | | 0
3 | updated_at | datetime(6) | 1 | | 0
