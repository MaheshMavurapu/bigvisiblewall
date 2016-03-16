| **Tool** | **Supported?** | **Website** | **Notes** |
|:---------|:---------------|:------------|:----------|
| Cruise   | Yes            | http://studios.thoughtworks.com/cruise-release-management |           |
| Hudson   | Yes            | https://hudson.dev.java.net/ | Add `cc.xml` to the end of the URL of your hudson dashboard to get the feed |
| CruiseControl.NET | Probably       | http://confluence.public.thoughtworks.org/display/CCNET/Welcome+to+CruiseControl.NET | Not tested, but CruiseControl.NET does provide cctray feeds |
| CruiseControl | Unknown        | http://cruisecontrol.sourceforge.net/ |  It isn't known if CruiseControl exports cctray feed |
| Bamboo   | No             | http://www.atlassian.com/software/bamboo/ | Bamboo doesn't seem to support cctray feeds: http://jira.atlassian.com/browse/BAM-2800 |
| CruiseControl.rb | Perhaps        | http://cruisecontrolrb.thoughtworks.com/ | CruiseControl.rb seems to provide cctray feeds, but they haven't been tested |

If you don't see your tool here, or have tested a feed from your build and found it to work, then please leave a comment.