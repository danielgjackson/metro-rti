# Tyne and Wear Metro Real-Time Information API Information 

## All Train Locations

Some brief nots on the newer API showing full map of live train locations.

From the site: https://www.nexus.org.uk/metro/updates

Assets:
- https://metro-rti.nexus.org.uk/api/geo/alert-icon.png
- https://metro-rti.nexus.org.uk/api/geo/warning-icon.png
- https://metro-rti.nexus.org.uk/api/geo/nexus-logo-metro.png
- https://metro-rti.nexus.org.uk/api/geo/train.png
- https://metro-rti.nexus.org.uk/api/geo/train-pointer.png

Page performance stats posted to:
- https://metro-rti.nexus.org.uk/cdn-cgi/rum?

Challenge request:
- https://metro-rti.nexus.org.uk/cdn-cgi/challenge-platform/h/g/jsd/r/.../...

The `Authorization: Bearer` header required for the Azure API requests. Parameter `d` is a timestamp in milliseconds since epoch.

- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/warning.kml?d=
- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/alerts.kml?d=
- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/metrolines.kml?d=
- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/metrostations.kml?d=
- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/trainstatuses.kml?d=
- https://app-metrortiapi-prod-001.azurewebsites.net/api/geo/traindirections.kml?d=

```
Host: app-metrortiapi-prod-001.azurewebsites.net
Origin: https://metro-rti.nexus.org.uk
Referer: https://metro-rti.nexus.org.uk/
Authorization: Bearer ...
```


## Per-platform train arrival API used by App

Information:
* App: https://play.google.com/store/apps/details?id=uk.co.nebulalabs.nexusnextgeneration
* API: `https://metro-rti.nexus.org.uk/api`
* user-agent: `okhttp/3.12.1`

Station information:
* `GET https://metro-rti.nexus.org.uk/api/stations`
  * `curl --user-agent "okhttp/3.12.1" https://metro-rti.nexus.org.uk/api/stations  > stations.json`
  * [data/stations.json](data/stations.json)

Platform information:
* `GET https://metro-rti.nexus.org.uk/api/stations/platforms`
  * `curl --user-agent "okhttp/3.12.1" https://metro-rti.nexus.org.uk/api/stations/platforms  > platforms.json`
  * [data/platforms.json](data/platforms.json)

Real-Time Information (refreshed every 2 minutes), examples:
* South Gosforth Platform 1: `GET https://metro-rti.nexus.org.uk/api/times/SGF/1`
  * `curl --user-agent "okhttp/3.12.1" https://metro-rti.nexus.org.uk/api/times/SGF/1  > times-sgf-1.json`
  * [data/times-sgf-1.json](data/times-sgf-1.json)
* Monument Platform 2: `GET https://metro-rti.nexus.org.uk/api/times/MTS/2`
  * `curl --user-agent "okhttp/3.12.1" https://metro-rti.nexus.org.uk/api/times/MTS/2  > times-mts-2.json`
  * [data/times-mts-2.json](data/times-mts-2.json)

Note: Monument (*MMT* from [Wikipedia](data/wikipedia-metro-stations.txt)), is split:
* *MTS* Monument South/North (Platforms 1 and 2)
* *MTW* Monument West/East (Platforms 3 and 4)

```json
[
  {
    "trn": "###",
    "lastEvent": "ARRIVED"|"DEPARTED",
    "lastEventLocation": "South Gosforth Platform 1",
    "lastEventTime": "YYYY-MM-DDThh:mm:ss",
    "dueIn": -1 // Arrived
  }, ...
]
```
