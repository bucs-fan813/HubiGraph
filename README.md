# Features
1. Graphing via [Google Charts](https://developers.google.com/chart) API
    - Line, Bar, Area, Time Line
    - Gauges
2. Weather Conditions and Forecast via PWS or OpenWeather
    - Fully Configurable Sub-tiles
3. Displaying graphs on a dashboard
    - Automatic child device ( [Hubigraph Tile Device](https://github.com/tchoward/Hubitat/blob/master/hubigraph_tile.groovy) ) creation
    - Add to dashboard via Graph attribute on an Attribute Tile
4. Support for all devices on Hub
5. Graph Configuration Support
    - Colors - (Titles, Labels, Lines, Axes, Backgrounds, etc)
    - Font Size - (Titles, Labels, Axes, etc)
    - Axes - (Location, Single/Dual, Number Tics, etc)
6. Hubigraph Tile Device
    - Auto install/uninstall child device with Graph Attributes
7. Real-time, Periodic Graph Updates
    - Real-time updates support sub-second updates
    - Periodic updates to reduce browser loading

# INSTALLATION
Due to the large number of files and the complexity involved to manually install HubiGraphs, I recommend using [HUBITAT PACKAGE MANAGER](https://community.hubitat.com/t/beta-hubitat-package-manager/38016) for install.

## LINKS
- [GITHUB REPOSITORY](https://github.com/tchoward/Hubitat)
- [HUBITAT PACKAGE MANAGER](https://community.hubitat.com/t/beta-hubitat-package-manager/38016)

## EXAMPLES AND SCREENSHOTS
### Time Graph with Overlay
[![Time Graph with Overlay](https://community.hubitat.com/uploads/default/optimized/3X/4/c/4c400721082e8bf7dbe140dfc03f0b82dacb26e4_2_1380x912.jpeg "Time Graph with Overlay")](https://community.hubitat.com/uploads/default/original/3X/4/c/4c400721082e8bf7dbe140dfc03f0b82dacb26e4.jpeg)

### Time Graph (Bar and Points)
[![Time Graph (Bar and Points)](https://community.hubitat.com/uploads/default/optimized/3X/c/3/c3afed7a04f92b5b02eedb384d6aa2bddf1de726_2_1380x894.jpeg "Time Graph (Bar and Points)")](https://community.hubitat.com/uploads/default/original/3X/c/3/c3afed7a04f92b5b02eedb384d6aa2bddf1de726.jpeg)

### TimeLine Showing Motion
[![TimeLine Showing Motion](https://community.hubitat.com/uploads/default/optimized/3X/6/8/68e6208fffc8730510eeb3e4919dbbc7f7f064f5_2_1380x776.jpeg "TimeLine Showing Motion")](https://community.hubitat.com/uploads/default/original/3X/6/8/68e6208fffc8730510eeb3e4919dbbc7f7f064f5.jpeg)

### Heat Map
[![Heat Map](https://community.hubitat.com/uploads/default/original/3X/2/6/26e485929235e743c1a39778c409e43b856ad8c5.jpeg "Heat Map")](https://community.hubitat.com/uploads/default/original/3X/2/6/26e485929235e743c1a39778c409e43b856ad8c5.jpeg)

### Weather Tile 2.0
[![Weather Tile 2.0](https://community.hubitat.com/uploads/default/optimized/3X/a/6/a6428c650f4ed26494bd058d60ecc3448242ff0b_2_864x1000.jpeg "Weather Tile 2.0")](https://community.hubitat.com/uploads/default/original/3X/a/6/a6428c650f4ed26494bd058d60ecc3448242ff0b.jpeg)

### Radar Tile
[![Radar Tile](https://community.hubitat.com/uploads/default/original/3X/1/f/1f744ec7fbef685484045a9cc8365f19bf99761c.jpeg "Radar Tile")](https://community.hubitat.com/uploads/default/original/3X/1/f/1f744ec7fbef685484045a9cc8365f19bf99761c.jpeg)

### Time Graph with Bars
[![Time Graph with Bars](https://community.hubitat.com/uploads/default/original/3X/b/0/b075a5a2421e23127953dd771b585062fe6d4c36.jpeg "Time Graph with Bars")](https://community.hubitat.com/uploads/default/original/3X/b/0/b075a5a2421e23127953dd771b585062fe6d4c36.jpeg)

[![Time Graph with Bars](https://community.hubitat.com/uploads/default/optimized/3X/f/c/fcac0a34ed34c948fc9a588095150ee63ad070f9_2_990x1000.jpeg "Time Graph with Bars")](https://community.hubitat.com/uploads/default/original/3X/f/c/fcac0a34ed34c948fc9a588095150ee63ad070f9.jpeg)

### Range Graph
[![Range Graph](https://community.hubitat.com/uploads/default/optimized/3X/5/f/5f6317b6a91a45749c3d9dc82ffef6d1ebb450f6_2_1150x1000.jpeg "Range Graph")](https://community.hubitat.com/uploads/default/original/3X/5/f/5f6317b6a91a45749c3d9dc82ffef6d1ebb450f6.jpeg)

[![Range Graph](https://community.hubitat.com/uploads/default/original/3X/e/1/e1697477a4b66e667b1d293f03cb1007a9ddf4bc.jpeg "Range Graph")](https://community.hubitat.com/uploads/default/original/3X/e/1/e1697477a4b66e667b1d293f03cb1007a9ddf4bc.jpeg)

[![Range Graph](https://community.hubitat.com/uploads/default/optimized/3X/c/d/cd6dce86f8ac8f9abb57c7628cfc1aab3bc4d17f_2_1380x808.jpeg "Range Graph")](https://community.hubitat.com/uploads/default/original/3X/c/d/cd6dce86f8ac8f9abb57c7628cfc1aab3bc4d17f.jpeg)

### Gauges
[![Gauges](https://community.hubitat.com/uploads/default/original/3X/6/f/6f3936597ac2867531feb6f216f9667ec55e378d.jpeg "Gauges")](https://community.hubitat.com/uploads/default/original/3X/6/f/6f3936597ac2867531feb6f216f9667ec55e378d.jpeg)

## DESIGN
It is important to understand the design of Hubigraphs in order to grasp both the advantages and the limitations of Hubigraphs.

1. Hubigraphs is designed to work on a dashboard. As such, when you load (or refresh) a dashboard, the "tile" queries the database for all events covering the graph's time period. This can be thousands of events (depending on your device). To be clear, it can take 20-30 seconds for the initial loading. That is the bad news.
2. Hubigraphs does not add any loading to the Hubitat Hub. Once a dashboard is loaded, the graphs update using the same endpoint as the dashboard. Therefore, all updates from that point forward DO NOT add any load to Hubitat, it is all on the device that is displaying the dashboard.
3. Hubigraphs uses [Google Charts](https://developers.google.com/chart) Therefore, all the limitations, advantages and ease/difficulty of use is inherited from Google Charts. In the alpha build, I tried to incorporate as many options as possible (axes, labels, titles, etc). Some people have asked for features that to be blunt would require designing and implementing my own graphing API.
4. Hubigraphs was designed to work without external devices. I enjoy playing around with [Grafana](https://grafana.com/), [Influxdb](https://www.influxdata.com/), and other technologies, but it has required too much maintenance and configuration. I designed Hubigraphs only within the confines of Hubitat (user apps, dashboard, etc). I have no plans to support other platforms (SharpTools, and other third party dashboards at this time). Do I care if you "steal" my code, modify it, and add native support for those platforms? Not at all (see my FAQ).

# FAQ
1. **"Your idea is stupid and slow and I don't like it"**
Don't use the app

2. **"Your app is crashing my Hub. I submitted a support ticket"**
Don't do that, the fine folks at hubitat do not maintain the app. This software is given free of charge with no support.

3. **"The latest update broke the app, FIX IT".** 
I do this for fun, please don't make it un-fun.

4. **"I have a great idea for a feature".** 
Go ahead and post it, I might get around to it...

5. **"You ignored my great idea".**
See #2

6. **"I hate you for getting my hopes up, your app is awful/buggy/stupid".**
Ok

7. **"Please fix your app, it's broken".**
All cards on the table, I built this app for my wife. I will continue to support and provide updates as long as she uses it.

8. **"I stole your code and made it soooo much better" Thanks. Please post it so I can start using it.

9. **"You are awfully sarcastic, I don't like you".** 
I have teenagers.

10. **"You stole the "Hubi" name, your app doesn't deserve it."** 
My daughter came up with it. If the hubitat owners object, I will change it.

11. **"Your latest fix made things worse."** 
I already covered this and See #9
