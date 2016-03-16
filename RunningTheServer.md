

# Starting the server #

Either [build it from source](http://code.google.com/p/bigvisiblewall/wiki/HowToBuild), or grab [the latest distro](http://code.google.com/p/bigvisiblewall/downloads/list).

Either way, once you have a distribution, just unzip it and either execute `run.sh` or `run.bat`.

## Proxy Servers ##
If you need to configure a proxy for access to your cctray feed:

```
 sh ./run.sh -proxy.host proxy.mycompany.co.uk -proxy.port 8080 
```

## Authentication ##
If your cctray sits behind basic auth:

```
sh ./run.sh -http.username cruise -http.password cruise
```

Eventually this will be configurable in app (I'll get the app to prompt for auth details if it gets a 401).

# Configuring what to display #

## Summary ##

| **Param** | **Valid Values** | **Description** |
|:----------|:-----------------|:----------------|
| source    | Any accessible URL | Defines which cctray feed to display. Multiple sources are allowed |
| display   | `grid, list, single, smart` | See [RunningTheServer#Different\_Display\_Options](RunningTheServer#Different_Display_Options.md) |
| cruiseSource | Any accessible URL | Defines a cruise cctray feed to display. Handles the tree implicit tree structure. Specify the depth to display as a comma seperated value after the URL to the feed. See [RunningTheServer#Cruise\_support](RunningTheServer#Cruise_support.md) for more details |

  * Navigate to the wall:

```
http://localhost:8080/?source=http://mycompany.com/cctray.xml
```

## Filtering ##

You can filter out builds by using a prefix, e.g.:

```
http://localhost:8080/?source=http://mycompany.com/cctray.xmll&prefix=myproject
```

only shows builds that begin with 'myproject'. You can specify multiple prefixes.

## Multiple Sources ##

You can specify multiple cctray sources:

```
http://localhost:8080/?source=http://mycompany.com/cctray.xml&source=http://myothercompany.com/cctray.xml
```

## Different Display Options ##

You can switch between three different display options using the `source=` option. The default display type is 'grid'.

### List style - `display=list` ###
![http://bigvisiblewall.googlecode.com/files/ListDisplayStyle.png](http://bigvisiblewall.googlecode.com/files/ListDisplayStyle.png)

### Grid style - `display=grid` ###
![http://bigvisiblewall.googlecode.com/files/GridDisplayStyle.png](http://bigvisiblewall.googlecode.com/files/GridDisplayStyle.png)

### Single build style (one build fills the whole screen)  `display=single` ###
![http://bigvisiblewall.googlecode.com/files/SingleDisplayStyle.png](http://bigvisiblewall.googlecode.com/files/SingleDisplayStyle.png)

## Cruise support ##

Big Visible Wall also has specific support for the CC Tray feeds which [Cruise](http://studios.thoughtworks.com/cruise-release-management) build tool serves up. Cruise takes each stage & step and puts them into a flat list inside the feed, but by using the `cruiseSource` param, Big Visible Wall can try and imply a hirearchy from the feed.

Lets imagine the following build structure:

```
Project 1
  --- Fast
             ---- Compile
             ---- Test
  --- Slow
             ---- Deploy
             ---- Test

Project 2
  --- Performance
          ---- SunOS
          ---- Irix
```

You specify a depth as part of the cruise source param, e.g.:

```
http://localhost:8080/?cruiseSource=http://somecruiseinstall/cctray.xml,2
```

By using a depth of '1', we only see `Project 1` and `Project 2`:

![http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth1.png](http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth1.png)

By using a depth of '2', we see `Project 1 :: Fast`, `Project 1 :: Slow` and `Project 2 :: Performance`:

![http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth2.png](http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth2.png)

And with a depth of '3', we see all the steps:

![http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth3.png](http://bigvisiblewall.googlecode.com/files/CruiseDisplayDepth3.png)

If you pull in sources from more than one location, you can use different depths for each cruise feed.