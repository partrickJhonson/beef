BeEF has several methods to determine the hooked browser's location.

### IP Geolocation

The enable IP Geolocation, download the MaxMind database:

```bash
curl -O http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz
gunzip GeoLiteCity.dat.gz && mkdir /opt/GeoIP && mv GeoLiteCity.dat /opt/GeoIP
```

Then edit `config.yaml` to enable IP Geolocation and specify the path to the database. For example:

```yaml
    geoip:
        enable: true
        database: '/opt/GeoIP/GeoLiteCity.dat'
```

### Modules

Several modules exist to determine the hooked browser's location.

**Geolocation**

The [[Geolocation|Module: Geolocation]] module will retrieve the physical location of the hooked browser using the Phonegap API.


**Get Geolocation**

The [[Get Geolocation|Module: Get Geolocation]] module will retrieve the physical location of the hooked browser using the Geo-location API. The user will be prompted to share their location with the hooked origin, unless the hooked origin has been white-listed previously.


**Get Physical Location**

The [[Get Physical Location|Module: Get Physical Location]] module will retrieve Geo-location information based on the neighboring wireless access points using commands encapsulated within a signed Java Applet. The user will be prompted to run the Java applet.

The details will include:

* GPS Coordinates details
* Street Address details

If the victim machine has a firewall that monitors outgoing connections (Zonealaram, LittleSnitch, etc), calls to Google maps will be alerted.
