---
layout: page
title: About
permalink: /about/
---

Debugging and testing java application on [Raspebby Pi](http://www.raspberrypi.org/) using [Pi4J libraries](http://pi4j.com/index.html) can be very difficult. Especially if you do not have your hardware yet, or if your process take several hours to change.

Mocking the Pi4J implementation may be usefull for small tests, but you may have to simulate a complex process. Such a process are too difficult to modelise with java code.

On the other hand, a lot of applications are available to modelise and simulate "real life" process. Those applications can run simulation without time restriction, it is possible to simulate, for example, the daily heat flow in a house in a few seconds. Most of them works with connected blocks. Each blocks have parameters, inputs and outputs.

Thanks to the new FMI (Fonctional Mock-up Interface) standard [FMI 2.0](https://www.fmi-standard.org/) it is possible to define a block called FMU (Functional Mock-up Unit). FMU are used for coupling of several simulation tools, each tool treats one part of a modular coupled problem. It is usefull to simulate heterogeneous system or to simulate Software-in-the-loop.

RaspInLoop provides a FMU implementation that allows java code, using Pi4J, to be in the simulation loop.

Have a look to the [Getting Started](/gettingstarted/) page have more information about  installation and usage.
