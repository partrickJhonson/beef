
### Introduction ###

The below details the Database Schema of BeEF.

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

```
sqlite> PRAGMA table_info(autoloader);
```
cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | command_id | integer | 0 |  | 0
2 | in_use | boolean | 0 |  | 0

```
sqlite> PRAGMA table_info(browser_details);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | session_id | text | 0 |  | 0
2 | detail_key | text | 0 |  | 0
3 | detail_value | text | 0 |  | 0

```
sqlite> PRAGMA table_info(command_modules);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | name | text | 0 |  | 0
2 | path | text | 0 |  | 0

```
sqlite> PRAGMA table_info(commands);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | command_module_id | integer | 0 |  | 0
2 | hooked_browser_id | integer | 0 |  | 0
3 | data | text | 0 |  | 0
4 | creationdate | datetime | 0 |  | 0
5 | label | text | 0 |  | 0
6 | instructions_sent | boolean | 0 | 0 | 0

```
sqlite> PRAGMA table_info(dns_rule);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | pattern | text | 0 |  | 0
2 | resource | text | 0 |  | 0
3 | response | text | 0 |  | 0
4 | callback | text | 0 |  | 0

```
sqlite> PRAGMA table_info(executions);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | session_id | text | 0 |  | 0       
2 | mod_count | integer | 0 |  | 0
3 | mod_successful | integer | 0 |  | 0
4 | mod_body | text | 0 |  | 0               
5 | exec_time | text | 0 |  | 0
6 | rule_token | text | 0 |  | 0  
7 | is_sent | boolean | 0 |  | 0  
    
```
sqlite> PRAGMA table_info(hooked_browsers);
```
cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | session | text | 0 |  | 0
2 | ip | text | 0 |  | 0
3 | firstseen | text | 0 |  | 0
4 | lastseen | text | 0 |  | 0
5 | httpheaders | text | 0 |  | 0
6 | domain | text | 0 |  | 0
7 | port | integer | 0 |  | 0
8 | count | integer | 0 |  | 0
9 | is_proxy | boolean | 0 |  | 0

```
sqlite> PRAGMA table_info(http);
```                                                                                                                                                                                             

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | request | text | 0 |  | 0
3 | allow_cross_domain | boolean | 0 | 1 | 0
4 | response_data | text | 0 |  | 0
5 | response_status_code | integer | 0 |  | 0
6 | response_status_text | text | 0 |  | 0
7 | response_port_status | text | 0 |  | 0
8 | response_headers | text | 0 |  | 0
9 | method | text | 0 |  | 0
10 | content_length | text | 0 | '0' | 0
11 | proto | text | 0 |  | 0
12 | domain | text | 0 |  | 0
13 | port | text | 0 |  | 0
14 | has_ran | text | 0 | 'waiting' | 0
15 | path | text | 0 |  | 0
16 | response_date | datetime | 0 |  | 0
17 | request_date | datetime | 0 |  | 0

```
sqlite> PRAGMA table_info(interceptors);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | ip | text | 0 |  | 0
2 | post_data | text | 0 |  | 0

```
sqlite> PRAGMA table_info(ipec_exploit);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | name | text | 0 |  | 0
2 | protocol | text | 0 |  | 0
3 | os | text | 0 |  | 0

```
sqlite> PRAGMA table_info(ipec_exploit_run);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | launched | boolean | 0 |  | 0
2 | http_headers | text | 0 |  | 0
3 | junk_size | text | 0 |  | 0

```
sqlite> PRAGMA table_info(logs);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | logtype | text | 0 |  | 0
2 | event | text | 0 |  | 0
3 | date | datetime | 0 |  | 0
4 | hooked_browser_id | integer | 0 |  | 0

```
sqlite> PRAGMA table_info(mass_mailer);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1

```
sqlite> PRAGMA table_info(network_hosts);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | ip | text | 0 |  | 0
3 | hostname | text | 0 |  | 0
4 | ntype | text | 0 |  | 0
5 | os | text | 0 |  | 0
6 | mac | text | 0 |  | 0
7 | lastseen | text | 0 |  | 0

```
sqlite> PRAGMA table_info(network_services);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | proto | text | 0 |  | 0
3 | ip | text | 0 |  | 0
4 | port | text | 0 |  | 0
5 | ntype | text | 0 |  | 0

```
sqlite> PRAGMA table_info(option_caches);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | name | text | 0 |  | 0
2 | value | text | 0 |  | 0

```
sqlite> PRAGMA table_info(results);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | command_id | integer | 0 |  | 0
2 | hooked_browser_id | integer | 0 |  | 0
3 | date | datetime | 0 |  | 0
4 | status | integer | 0 |  | 0
5 | data | text | 0 |  | 0

```
sqlite> PRAGMA table_info(rtc_manage);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | message | text | 0 |  | 0
3 | has_sent | text | 0 | 'waiting' | 0

```
sqlite> PRAGMA table_info(rtc_module_status);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | command_module_id | integer | 0 |  | 0
3 | target_hooked_browser_id | integer | 0 |  | 0
4 | status | text | 0 |  | 0

```
sqlite> PRAGMA table_info(rtc_signal);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | target_hooked_browser_id | integer | 0 |  | 0
3 | signal | text | 0 |  | 0
4 | has_sent | text | 0 | 'waiting' | 0

```
sqlite> PRAGMA table_info(rtc_status);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | target_hooked_browser_id | integer | 0 |  | 0
3 | status | text | 0 |  | 0

```
sqlite> PRAGMA table_info(rules);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | name | text | 0 |  | 0
2 | author | text | 0 |  | 0
3 | browser | text | 0 |  | 0
4 | browser_version | text | 0 |  | 0
5 | os | text | 0 |  | 0
6 | os_version | text | 0 |  | 0
7 | modules | text | 0 |  | 0
8 | execution_order | text | 0 |  | 0
9 | execution_delay | text | 0 |  | 0
10 | chain_mode | text | 0 |  | 0

```
sqlite> PRAGMA table_info(schema_migrations);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | version | varchar | 1 |  | 1

```
sqlite> PRAGMA table_info(web_cloner);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | uri | text | 0 |  | 0
2 | mount | text | 0 |  | 0

```
sqlite> PRAGMA table_info(xssrays_detail);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | vector_name | text | 0 |  | 0
3 | vector_method | text | 0 |  | 0
4 | vector_poc | text | 0 |  | 0

```
sqlite> PRAGMA table_info(xssrays_scan);
```

cid | name | type | notnull | default | pk
--- | --- | --- | --- | --- | ---
0 | id | integer | 1 |  | 1
1 | hooked_browser_id | integer | 0 |  | 0
2 | scan_start | datetime | 0 |  | 0
3 | scan_finish | datetime | 0 |  | 0
4 | domain | text | 0 |  | 0
5 | cross_domain | text | 0 |  | 0
6 | clean_timeout | integer | 0 |  | 0
7 | is_started | boolean | 0 |  | 0
8 | is_finished | boolean | 0 |  | 0

        
