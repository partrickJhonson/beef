##Summary
* **Objective**: Get the Internal IP of the hooked system
* **Date**: June 2012
* **Authors**: antisnatchor
* **Browsers**: IE, Opera, Firefox (User is notified on Chrome and Safari)
* [[Code|https://github.com/beefproject/beef/tree/master/modules/host/get_internal_ip]]

##Internal Working

This applet is adapted from [Lars Kindermann applet](http://reglos.de/myaddress/MyAddress.html) and basically just use the Java Socket class to get the host address:
```java
        try {
            String str1 = new Socket(str2, i).getLocalAddress().getHostAddress();
            if (!str1.equals("255.255.255.255")) obj = str1;
        } catch (SecurityException localSecurityException) {
            obj = "FORBIDDEN";
        } catch (Exception localException1) {
            obj = "ERROR";
        }
```

## Screenshots

[[Images/module-get-internal-ip.png|align=center]]

## References

* [Lars Kindermann IP address Applet](http://reglos.de/myaddress/MyAddress.html)

