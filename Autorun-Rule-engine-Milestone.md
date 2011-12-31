Implement a method to automatically execute a set of modules based on previous module results. The process is data driven and it is suggested that the drools rule engine be used. 

The database needs to be changed to support a tag-value system. For example, a hooked browser could have a tag of ‘Internal_IP_Address’ that could have the value of '192.168.1.5’. Next, the rules engine would fire all the modules that only require 'Internal_IP_Address' as the input and those results would set further tags. Following this, those values would fire another round of modules. 
