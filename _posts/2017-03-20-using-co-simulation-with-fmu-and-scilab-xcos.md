---
title: "Using Co-simulation with FMU and scilab/xcos"
date: "2017-03-20 22:57"
subtitle: Using scilab/xcos to simulate BlinkingGpioExample
layout: default
modal-id: 4
date: 2017-03-20
img: ptolemywired.png
thumbnail: Xcos-stepper-thumbnail.png
alt: step motor with XCos
project-date: March 2020
client: Eclipse Plugin
category: External Simulation
description:
---
## Xcos
Xcos (from [Scilab](http://www.scilab.org/)) is a graphical dynamical system modeler and simulator. Users can create block diagrams to model and simulate the dynamics of hybrid dynamical systems both continuous and discrete time.

RaspInLoop uses the Fonctional Mockup Interface (FMI) to communicate with such a simulator and the eclipse's debugger. Xcos doesn't provide module pre-installed to use FMI. We have to install it by ourselves.

The module is called "Xcos FMU wrapper" and is available on the scilab forge. Unfortunately, support for FMI 2.0 (which is required for RaspInloop) is still on development. So installation won't be so easy.

## Let's start:

Download lastest sources of the "Xcos FMU wrapper" module in zip https://forge.scilab.org/index.php/p/fmu-wrapper/source/download/master/
Be sure to download latest version(~	2016-11-22  ) which include support fro FMI 2.0 (and scilab 6.0 if you use it)

Unzip in a local directory. ex: *C:\Users\Fred\Documents\RIL\fmu-wrapper-master*

Then, open scilab, type
```
cd C:\Users\Fred\Documents\RIL\fmu-wrapper-master
exec('C:\Users\Fred\Documents\RIL\fmu-wrapper-master\builder.sce',-1)
exec('C:\Users\Fred\Documents\RIL\fmu-wrapper-master\loader.sce',-1)
```
You can now start xcos
You should have a new entry in you "palette browser"
![palette browser]({{ site.baseurl }}/img/tutorials/Xcos-palettebrowser.png)

  Note: to avoid to load module manualy at every startup, you could add this:

```
cd C:\Users\Fred\Documents\RIL\fmu-wrapper-master
exec('C:\Users\Fred\Documents\RIL\fmu-wrapper-master\loader.sce',-1)
```

in your *C:\Users\Fred\AppData\Roaming\Scilab\scilab-5.5.2\.scilab* file.

## Finally

You may then, drop the FMInterface block into your diagram.
Double click on the block to select the previously saved FMU ([see tuto]({{ site.baseurl }}/_post/2016-04-05-example-BlinkGpioExample.md))
![Double click]({{ site.baseurl }}/img/tutorials/Xcos-selectFmu.png)

Once selected the Block will reflect input/output defined in FMU
![full diagram]({{ site.baseurl }}/img/tutorials/Xcos-stepper.png)
