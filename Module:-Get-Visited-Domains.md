##Summary

* **Objective**: This module will retrieve rapid history extraction through non-destructive cache timing.Based on work done at http://lcamtuf.coredump.cx/cachetime/
* **Date**: March 2012
* **Author**: keith_lee
* **Browsers**: Firefox / IE
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/get_visited_domains)

##Internal Working

This module uses a trick discovered by Michal Zalewski in 2012 to detect if the browser have visited a given domain by abusing the browser's cache : the module load a javascript (for Firefox) or a picture (for IE) and look the response time. If the response time is very short, the file was probably already in browser's cache and it is thus not the first visit of the domain.

The module embeds a list of Javascript and Image file for different domains (see [here](https://github.com/beefproject/beef/blob/master/modules/browser/get_visited_domains/command.js). As this list was done by Michal Zalewski in early 2012, it may have changed and thus rendering this module less accurate.

##Feedback

##References

* http://lcamtuf.coredump.cx/cachetime/