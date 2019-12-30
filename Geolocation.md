BeEF has several methods to determine the hooked browser's location.

### IP Geolocation

To enable IP Geolocation, download the MaxMind database. This can be achieved by using the `./update-geoipdb` script.

```bash
./update-geoipdb
```

By default, the MaxMind database is installed into `/opt/GeoIP`. If you opt to install the database manually, or change the page, you'll also need to update the path in `config.yaml` to the new path:

```yaml
    geoip:
        enable: true
        database: '/opt/GeoIP/GeoLite2-City.mmdb'
```

### Modules

Several modules exist to determine the hooked browser's location.

**Geolocation**

The [[Geolocation|Module: Geolocation]] module will retrieve the physical location of the hooked browser using the Phonegap API.


**Get Geolocation**

The [[Get Geolocation|Module: Get Geolocation]] module will retrieve the physical location of the hooked browser using the Geo-location API. The user will be prompted to share their location with the hooked origin, unless the hooked origin has been white-listed previously.


**Get Physical Location**

The [[Get Physical Location|Module: Get Physical Location]] module will retrieve Geo-location information based on the neighboring wireless access points using commands encapsulated within a self-signed Java Applet. The user will be prompted to run the Java applet.

The details will include:

* GPS Coordinates details
* Street Address details

If the victim machine has a firewall that monitors outgoing connections (Zonealaram, LittleSnitch, etc), calls to Google maps will be alerted.

Note that modern Java (as of Java 7u51) will outright refuse to execute self-signed Java applets unless they're added to the exception list.
