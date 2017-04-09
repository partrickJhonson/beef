## Summary

* **Objective** : This module attempts to detect software installed on the host by using [Internet Explorer XMLDOM XXE](https://soroush.secproject.com/blog/2013/04/microsoft-xmldom-in-ie-can-divulge-information-of-local-drivenetwork-in-error-messages/) discovered by Soroush Dalili (@irsdl). If the XMLDOM XXE technique fails, the module falls back to using the 'res' protocol handler to load known resource images from EXE/DLL files. It also attempts to enumerate installed patches if service pack uninstall files are present on the host (WinXP only).
* **Authors**: bcoles
* **Browser**: IE
* [Code](https://github.com/beefproject/beef/tree/master/modules/host/detect_software)


## Internal working

This module abuses an XXE vulnerability ([CVE-2013-7331](https://www.cvedetails.com/cve/cve-2013-7331)) in the `loadXML()` method of the `ActiveXObject("Microsoft.XMLDOM")` object in Internet Explorer to determine whether specific folders are present on the system.

This vulnerability was patched in [MS14-05](https://technet.microsoft.com/en-us/library/security/ms14-052.aspx) in September 2014.

See the [source code](https://github.com/beefproject/beef/tree/master/modules/host/detect_software) for more information.


## References

* [Internet Explorer XMLDOM XXE](https://soroush.secproject.com/blog/2013/04/microsoft-xmldom-in-ie-can-divulge-information-of-local-drivenetwork-in-error-messages/)
* [CVE-2013-7331](https://www.cvedetails.com/cve/cve-2013-7331)
* [MS14-05](https://technet.microsoft.com/en-us/library/security/ms14-052.aspx)
