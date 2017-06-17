---
layout: page
title: About
permalink: /about/
---

Debugging and testing Java application on [Raspebby Pi](http://www.raspberrypi.org/) using [Pi4J libraries](http://pi4j.com/index.html) can be very difficult. Especially if you do not have your hardware yet, or if your process takes several hours to change.

Mocking the Pi4J implementation may be useful for small tests, but you may have to simulate a complex process. Such a process are too difficult to model with java code.

On the other hand, a lot of applications are available to model and simulate “real life” process. Those applications can run a simulation without time restriction, it is possible to simulate, for example, the daily heat flow in a house in a few seconds. Most of them work with connected blocks. Each block has parameters, inputs, and outputs.

Thanks to the new FMI (Function Mock-up Interface) standard [FMI 2.0](https://www.fmi-standard.org/) it is possible to define a block called FMU (Functional Mock-up Unit). FMU are used for coupling of several simulation tools, each tool treats one part of a modular coupled problem. It is useful to simulate a heterogeneous system or to simulate Software-in-the-loop.

RaspInLoop provides an FMU implementation that allows Java code, using Pi4J, to be in the simulation loop.

Have a look to the [How It Works](/howitworks/), [Tutorials](/tutorial/) pages have more information about installation and usage.
