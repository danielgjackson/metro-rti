# Tyne and Wear Metro Real-Time Information API Information 

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
