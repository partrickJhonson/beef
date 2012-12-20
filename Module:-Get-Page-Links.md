##Summary
* **Objective**: This module will retrieve HREFs from the target page.
* **Date**: ???
* **Authors**: vo
* **Browsers**: All
* [[Code|https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/get_page_links]]

##Internal Working

This module uses the [[_beef.dom.getLinks_ method|https://github.com/beefproject/beef/blob/master/core/main/client/dom.js]] to gather all links in the hooked  web page. This method uses the **document.links** function to gather this information.

##Feedback