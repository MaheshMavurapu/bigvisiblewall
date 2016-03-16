

## Does this support Hudson? ##

Yes - but the cctray feed is hidden away. You'll need to add 'cc.xml' to the URL for your Hudson build:

```
http://myhudsonserver/cc.xml
```

## Does this support Cruise? ##

Yes - although once again only via a cctray feed, so much of the structure (pipelines) of the build has to be implied. There is an experimental `cruiseSource` parameter which will add better cruise-specific source

## Does Big Visible Wall support Some Other Build Tool? ##

Maybe. The goal is to support cctray feeds from all the major build tools - however I've had limited ability to test with the multitude of build tools out there. Check the SupportedBuildTools page for more information

## Why only support cctray? ##

Many different tools out there output cctray feeds. These feeds are relatively uniform, so allow me to create a tool which supports the largest group of users.

## Will you support other types of feed? ##

Perhaps.

## What version of Java is supported? ##

Currently, due to [this issue](http://code.google.com/p/bigvisiblewall/issues/detail?id=1), a Java 6 runtime is required. It is hoped that this requirement can be relaxed once this issue is resolved.