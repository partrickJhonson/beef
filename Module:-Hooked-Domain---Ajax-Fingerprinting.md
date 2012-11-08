## Summary

* **Objective**: Fingerprint Ajax and JS libraries present on the hooked page.
* **Date**: ?
* **Author**: qswain
* **Browser**: Firefox, Safari
* [Code](https://github.com/beefproject/beef/tree/master/modules/browser/hooked_domain/ajax_fingerprint)

## Internal Working 

This module analyses all script tags on the page and compare them with a list of script name for different libraries:
```javascript
     var fingerprints = {
             "Prototype":new Array("prototype"),
             "script.aculous":new Array("builder","controls","dragdrop","effects","scriptaculous","slider","unittest"),
             "Dojo":new Array("dojo.uncompressed","uncompressed","dojo"),
             "DWR":new Array("auth","engine","util"),
             "Moo.fx/":new Array("Moo","Function","Array","String","Element","Fx","Dom","Ajax","Drag","Windows","Cookie","Json","Sortable","Fxpack","Fxutils","Fxtransition","Tips","Accordion"),
             "Rico": new Array("rico","ricoAjax","ricoCommon","ricoEffects","ricoBehaviours","ricoDragDrop","ricoComponents"),
             "Mootools":new Array("mootools","mootools-core-1.4-full","mootools-more-1.4-full"),
             "Mochikit":new Array("Mochikit"),
             "Yahoo UI!": new Array("animation","autocomplete","calendar","connection","container","dom","enevet","logger","menu","slider","tabview","treeview","utilities","yahoo","yahoo-dom-event"),
             "xjax":new Array("xajax","xajax_uncompressed"),
             "GWT": new Array("gwt","search-results"),
             "Atlas": new Array("AtlasRuntime","AtlasBindings","AtlasCompat","AtlasCompat2"),
             "jquery":new Array("jquery","jquery-latest","jquery-latest","jquery-1.5"),
             "ExtJS":new Array("ext-all"),
             "Prettify":new Array("prettify"),
             "Spry": new Array("SpryTabbedPanels","SpryDOMUtils","SpryData","SpryXML","SpryUtils","SpryURLUtils","SpryDataExtensions","SpryDataShell","SpryEffects","SpryPagedView","SpryXML"),
             "Google JS Libs":new Array("xpath","urchin","ga"),
             "Libxmlrequest":new Array("libxmlrequest"),
             "jx":new Array ("jx","jxs"),
             "bajax":new Array("bajax"),
             "AJS": new Array ("AJS","AJS_fx"),
             "Greybox":new Array("gb_scripts.js"),
             "Qooxdoo":new Array("qx.website-devel","qooxdoo-1.6","qooxdoo-1.5.1","qxserver","q","q.domain","q.sticky","q.placeholder","shCore","shBrushScript"),            
     };
```

## Feedback


## References