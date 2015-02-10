---
layout: page
title: Install
permalink: /Install/
---

#Install eclipse plugin

The plugin is compatible with eclipse Juno and higher (4.2)

update site url : `www.raspinloop.org/data/updates/4.2`

![new update site]({{ site.baseurl }}/images/updatesite.png)

![select feature]({{ site.baseurl }}/images/featureselection.png)

The current plugin is not signed yet, so you will have to accept it...

![unsigned plugin]({{ site.baseurl }}/images/unsignedplugin.png)

Then restart eclipse...

#start your application

In order to debug you Pi4J application, you have to create a new debug configuration.
Choose RIL-Simulate --> new 

Choose your project main class and click on "Debug"

![create debug config]({{ site.baseurl }}/images/createdebugconfiguration.png)

When console print this message : `INFO  [Server] Starting the simple server...` debugger is ready to interract with simulation tool

![debugging]({{ site.baseurl }}/images/debugging.png)



See [tutorials]({{ site.baseurl }}/tutorial/) to know how to configure simulation tool....

