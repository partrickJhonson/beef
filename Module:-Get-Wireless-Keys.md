### Summary

This module will retrieve the wireless profiles from the target system (Windows Vista and Windows 7 only).

Note that this module makes use of an unsigned Java applet. The target browser must have Java enabled and must allow loading unsigned Java applets. Modern Java and modern browsers do not permit loading unsigned Java applets and will raise a lot of warnings.

You will need to copy the results to 'exported_wlan_profiles.xml' and then reimport back into your Windows Vista/7 computers by running the command `netsh wlan add profile filename="exported_wlan_profiles.xml"`

After that, just launch and connect to the wireless network without any password prompt.
