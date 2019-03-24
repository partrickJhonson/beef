### Summary

This module will retrieve the wireless profiles from the target system (Windows Vista and Windows 7 only) using an unsigned Java applet.

Note that modern Java (as of Java 7u51) will outright refuse to execute unsigned Java applets, and will also reject self-signed Java applets unless they're added to the exception list.

You will need to copy the results to 'exported_wlan_profiles.xml' and then reimport back into your Windows Vista/7 computers by running the command `netsh wlan add profile filename="exported_wlan_profiles.xml"`

After that, just launch and connect to the wireless network without any password prompt.
