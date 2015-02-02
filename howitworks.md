---
layout: page
title: How It Works
permalink: /howitworks/
---

## Co-simulation
![overview]({{ site.baseurl }}/images/hiw-overview.png)

The intention is to provide a coupling between simulation tools and a running java application in eclipse. The data exchange between those systems is restricted to discrete communication points. In the time between two communication points, the java application is waiting. Master algorithms (in simulation tool) control the data exchange ans synchonization between itself and the java application (slave).




#FMU
![fmu]({{ site.baseurl }}/images/hiw-fmu.png)

FMU is a zipped file ended with .fmu, it contains, among other, a dynamic library (.dll or a.so) and a descriptior (.xml).


Simulation tools compatible with the FMI 2.0 for Co-Simulation are able to import such a library as a model block and 'link' it with other blocks in current model. After import, tool will call exported functions in order to get informations, initialize and run the simulation of the model.
Each library's function call is relayed (using tcp/ip) to a listening java application.




#launcher & eclipse plugin

![plugin]({{ site.baseurl }}/images/hiw-plugin.png)

In order to communicate with the FMU library, a java application must be running and listening.This application is called "launcher". It is responsible to launch a Pi4J program, substitude the Pi4J implementation and answer to the FMI request called by the simulation tool.



Integration into eclipse is done via plugin mechanism. Currently, The only extention is a run/debug launcher.