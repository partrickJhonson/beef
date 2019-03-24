## Summary

This module retrieves basic information about the host system using an unsigned Java applet.

The details include:

- Operating system details
- Java VM details
- NIC names and IP
- Number of processors
- Amount of memory
- Screen display modes

Note that modern Java (as of Java 7u51) will outright refuse to execute unsigned Java applets, and will also reject self-signed Java applets unless they're added to the exception list.

## Screenshots

[[Images/module-get-systeminfo.png|align=center]]