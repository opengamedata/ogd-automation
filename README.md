# opengamedata-automation

A repository for automation scripts to sync OGD logs from MySQL to BigQuery.

Setup:

* Install python3 for your environment
* Install python dependencies: "pip3 install -r requirements.txt"
* Copy `config.py.template` to `config.py` set server/authentication data and the source & destination db tables
* Download the authentication key needed for the BigQuery project. Save it as a .json file in the `config` directory and ensure the file path is defined in `config.py`

```bash
usage: <python> main.py <game> --max-days <count>

<python> is your python command.
<game> is the game whose data you wish to move to BigQuery
<count> is the max number of days-worth of data you wish to move
```

These processes are also set up to run automatically in GitHub actions.
Current workflows are configured to run at the following times:

| Time (UTC) | Time (Central) | Time (Central, Daylight) | Frequency | Game                 | Status  |
| ---        | ---            | ---                      | ---       | ---                  | ---     |
|  8:40      | 2:40 (AM)      | 3:40 (AM)                | Daily     | ANSWER_CAMPUS        | [![Answer Campus][Answer Campus Badge]][Answer Campus Link]    |
|  9:00      | 3:00 (AM)      | 4:00 (AM)                | Daily     | AQUALAB              | [![Aqualab][Aqualab Badge]][Aqualab Link]                      |
|  8:55      | 2:55 (AM)      | 3:55 (AM)                | Daily     | AYCET                | [![All You Can ET][All You Can ET Badge]][All You Can ET Link] |
|  9:05      | 3:05 (AM)      | 4:05 (AM)                | Daily     | BACTERIA             | [![Bacteria][Bacteria Badge]][Bacteria Link] |
| 10:45      | 4:45 (AM)      | 5:45 (AM)                | Daily     | BALLOON              | [![Balloon][Balloon Badge]][Balloon Link] |
|  9:10      | 3:10 (AM)      | 4:10 (AM)                | Daily     | BLOOM                | [![Bloom][Bloom Badge]][Bloom Link] |
|  11:25     | 5:25 (AM)      | 6:25 (AM)                | Daily     | CONECTADO            | [![Conectado][Conectado Badge]][Conectado Link] |
|  8:50      | 2:50 (AM)      | 3:50 (AM)                | Daily     | CRUSHSTATIONS        | [![CrushStations][CrushStations Badge]][CrushStations Link] |
|  9:15      | 3:15 (AM)      | 4:15 (AM)                | Daily     | CRYSTAL              | [![Crystal][Crystal Badge]][Crystal Link] |
|  9:20      | 3:20 (AM)      | 4:20 (AM)                | Daily     | CYCLE_CARBON         | [![Carbon Cycle][Carbon Cycle Badge]][Carbon Cycle Link] |
|  9:25      | 3:25 (AM)      | 4:25 (AM)                | Daily     | CYCLE_NITROGEN       | [![Nitrogen Cycle][Nitrogen Cycle Badge]][Nitrogen Cycle Link] |
|  9:30      | 3:30 (AM)      | 4:30 (AM)                | Daily     | CYCLE_WATER          | [![Water Cycle][Water Cycle Badge]][Water Cycle Link] |
|  9:35      | 3:35 (AM)      | 4:35 (AM)                | Daily     | EARTHQUAKE           | [![Earthquake][Earthquake Badge]][Earthquake Link] |
|  11:15     | 5:15 (AM)      | 6:15 (AM)                | Daily     | ASTRO                | [![Ex Sidera][Ex Sidera Badge]][Ex Sidera Link] |
|  8:45      | 2:45 (AM)      | 3:45 (AM)                | Daily     | GWAKKAMOLE           | [![Gwakkamole][Gwakkamole Badge]][Gwakkamole Link] |
|  9:40      | 3:40 (AM)      | 4:40 (AM)                | Daily     | ICECUBE              | [![Icecube][Icecube Badge]][Icecube Link] |
|  9:45      | 3:45 (AM)      | 4:45 (AM)                | Daily     | JOURNALISM           | [![Journalism][Journalism Badge]][Journalism Link] |
|  9:50      | 3:50 (AM)      | 4:50 (AM)                | Daily     | JOWILDER             | [![Jo Wilder][Jo Wilder Badge]][Jo Wilder Link] |
|  9:55      | 3:55 (AM)      | 4:55 (AM)                | Daily     | LAKELAND             | [![Lakeland][Lakeland Badge]][Lakeland Link] |
| 10:00      | 4:00 (AM)      | 5:00 (AM)                | Daily     | MAGNET               | [![Magnet][Magnet Badge]][Magnet Link] |
| 10:05      | 4:05 (AM)      | 5:05 (AM)                | Daily     | MASHOPOLIS           | [![Mashopolis][Mashopolis Badge]][Mashopolis Link] |
| 11:05      | 5:05 (AM)      | 6:05 (AM)                | Weekly    | MATCH                | [![Match][Match Badge]][Match Link] |
| 10:10      | 4:10 (AM)      | 5:10 (AM)                | Daily     | PENGUINS             | [![Penguins][Penguins Badge]][Penguins Link] |
| 11:10      | 5:10 (AM)      | 6:10 (AM)                | Daily     | PENNYCOOK            | [![Pennycook][Pennycook Badge]][Pennycook Link] |
| 10:15      | 4:15 (AM)      | 5:15 (AM)                | Daily     | SHADOWSPECT          | [![Shadowspect][Shadowspect Badge]][Shadowspect Link] |
| 10:20      | 4:20 (AM)      | 5:20 (AM)                | Daily     | SHIPWRECKS           | [![Shipwrecks][Shipwrecks Badge]][Shipwrecks Link] |
| 10:55      | 4:55 (AM)      | 5:55 (AM)                | Weekly    | SLIDE                | [![Slide][Slide Badge]][Slide Link] |
| 11:00      | 5:00 (AM)      | 6:00 (AM)                | Weekly    | STACK                | [![Stack][Stack Badge]][Stack Link] |
| 10:25      | 4:25 (AM)      | 5:25 (AM)                | Daily     | THERMOLAB            | [![Thermo Lab][Thermo Lab Badge]][Thermo Lab Link] |
| 10:30      | 4:30 (AM)      | 5:30 (AM)                | Daily     | TRANSFORMATION_QUEST | [![Transformations Quest][Transformations Quest Badge]][Transformations Quest Link] |
| 11:20      | 5:20 (AM)      | 6:20 (AM)                | Daily     | TE_BACTERIA          | ![Tiny Earth Bacteria][Tiny Earth Bacteria Badge] |
| 10:35      | 4:35 (AM)      | 5:35 (AM)                | Daily     | WAVES                | [![Waves][Waves Badge]][Waves Link] |
| 10:50      | 4:50 (AM)      | 5:50 (AM)                | Daily     | WEATHER_STATION      | [![Weather Station][Weather Station Badge]][Weather Station Link] |
| 10:40      | 4:40 (AM)      | 5:40 (AM)                | Daily     | WIND                 | [![Wind][Wind Badge]][Wind Link] |

Current latest run: 11:20 UTC/5:20 CST

Last keep-alive on 03/01/26

<!-- Reference links -->

[Answer Campus Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/answer_campus.yml/badge.svg
[Answer Campus Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/answer_campus.yml
[Aqualab Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/aqualab.yml/badge.svg
[Aqualab Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/aqualab.yml
[All You Can ET Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/aycet.yml/badge.svg
[All You Can ET Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/aycet.yml
[Bacteria Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/bacteria.yml/badge.svg
[Bacteria Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/bacteria.yml
[Balloon Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/balloon.yml/badge.svg
[Balloon Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/balloon.yml
[Bloom Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/bloom.yml/badge.svg
[Bloom Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/bloom.yml
[Conectado Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/conectado.yml/badge.svg
[Conectado Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/conectado.yml
[CrushStations Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/crushstations.yml/badge.svg
[CrushStations Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/crushstations.yml
[Crystal Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/crystal.yml/badge.svg
[Crystal Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/crystal.yml
[Carbon Cycle Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_carbon.yml/badge.svg
[Carbon Cycle Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_carbon.yml
[Nitrogen Cycle Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_nitrogen.yml/badge.svg
[Nitrogen Cycle Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_nitrogen.yml
[Water Cycle Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_water.yml/badge.svg
[Water Cycle Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/cycle_water.yml
[Earthquake Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/earthquake.yml/badge.svg
[Earthquake Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/earthquake.yml
[Ex Sidera Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/astro.yml/badge.svg
[Ex Sidera Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/astro.yml
[Gwakkamole Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/gwakkamole.yml/badge.svg
[Gwakkamole Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/gwakkamole.yml
[Icecube Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/icecube.yml/badge.svg
[Icecube Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/icecube.yml
[Journalism Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/journalism.yml/badge.svg
[Journalism Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/journalism.yml
[Jo Wilder Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/jowilder.yml/badge.svg
[Jo Wilder Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/jowilder.yml
[Lakeland Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/lakeland.yml/badge.svg
[Lakeland Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/lakeland.yml
[Magnet Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/magnet.yml/badge.svg
[Magnet Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/magnet.yml
[Mashopolis Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/mashopolis.yml/badge.svg
[Mashopolis Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/mashopolis.yml
[Match Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/match.yml/badge.svg
[Match Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/match.yml
[Penguins Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/penguins.yml/badge.svg
[Penguins Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/penguins.yml
[Pennycook Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/pennycook.yml/badge.svg
[Pennycook Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/pennycook.yml
[Shadowspect Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/shadowspect.yml/badge.svg
[Shadowspect Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/shadowspect.yml
[Shipwrecks Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/shipwrecks.yml/badge.svg
[Shipwrecks Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/shipwrecks.yml
[Slide Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/slide.yml/badge.svg
[Slide Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/slide.yml
[Stack Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/stack.yml/badge.svg
[Stack Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/stack.yml
[Thermo Lab Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/thermolab.yml/badge.svg
[Thermo Lab Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/thermolab.yml
[Transformations Quest Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/transformation_quest.yml/badge.svg
[Transformations Quest Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/transformation_quest.yml
[Tiny Earth Bacteria Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/tinyearth_bacteria.yml/badge.svg
[Tiny Earth Bacteria Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/tinyearth_bacteria.yml
[Waves Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/waves.yml/badge.svg
[Waves Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/waves.yml
[Weather Station Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/weather_station.yml/badge.svg
[Weather Station Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/weather_station.yml
[Wind Badge]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/wind.yml/badge.svg
[Wind Link]: https://github.com/opengamedata/opengamedata-automation/actions/workflows/wind.yml