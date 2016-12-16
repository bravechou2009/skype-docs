# Gathering Media Logs from the Skype Web SDK or Conversation Control

**In this article:**

- [Media logs in Internet Explorer](#ie)
- [Media logs in Microsoft Edge](#edge)
- [Media logs in Safari](#safari)
- [Media logs in other browsers](#other)
- [Related Topics](#related-topics)

If your failing scenario involves using Audio/Video with the Skype Web SDK or Conversation Control, please include the appropriate media logs in your bug report. Unfortunately the media logs are in a binary format and require specific software and symbol files to view and interpret so you will not be able to view the media log on your own.

Depending on the browser and OS in which you're running the Skype Web SDK or Conversation Control, the location of media logs will vary. See below for the instructions on gathering media logs specific to your browser.

<a href="ie"></a>
## Media logs in Internet Explorer

Using Audio/Video in Internet Explorer requires the Skype For Business media plugin. The location of the logs will depend on where the plugin is installed. If the plugin is installed in the default install location on a Windows machine, the path of the log files looks like this:

>**%LOCALAPPDATA%\Microsoft\SkypeForBusinessPlugin\Tracing**

After reproducing the scenario, close the browser, navigate to this directory and select the 2 most recently modified files with the extension **.etl**. Their names should look like this:

>**PluginHost_MediaStack-\<BUILD\_NUMBER\>-releases_CL2016_R12-x86fre-U.etl** <br>
**PluginHost_MediaStackETW-\<BUILD\_NUMBER\>-releases_CL2016_R12-x86fre-U.etl**

Include both files in the issue report.

<a href="edge"></a>
## Media logs in Microsoft Edge

Using Audio/Video in the Skype Web SDK in Microsoft Edge uses the Microsoft Edge native implementation of the ORTC (Object Real-Time Communications) protocol. In order to collect media logs for Audio/Video activity in Microsoft Edge, you must first enable Microsoft Edge ORTC media logging by setting a registry key. On a Windows machine, you can do so by running this script: 

[Enable ORTC media logging in Microsoft Edge](../../../utils/EnableEdgeLogging.ps1)

This script will enable media logging in Microsoft Edge until you delete or set the registry key added here to 0.

After enabling media logging in this way, restart Microsoft Edge, reproduce the failing scenario, close the the browser and run the following script:

[Save most recent Microsoft Edge media logs](../../../utils/pullEdgeLogs-external.ps1)

This will copy the 2 most recent media log files from the default location where Microsoft Edge ORTC media logs are written into a folder in the home directory of your machine. Copy the entire folder containing these logs and include it in the issue report.

<a href="safari"></a>
## Media logs in Safari

Audio/Video support in Safari is provided by the Skype for Business Meetings Plugin just as in IE, so the Safari plugin media logs are available in a tracing directory within the directory where the plugin is installed, and should have names similar to the plugin media logs in IE.

<a href="other"></a>
## Media logs in Other Browsers

Once AV support expands to other browsers like Chrome and Firefox, we will add instructions on capturing media logs for these browsers.

<a href="related-topics"></a>
## Related topics
- [Release Notes](../../ReleaseNotes.md)