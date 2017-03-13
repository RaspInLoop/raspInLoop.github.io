---
layout: "post"
title: "Standalone BlinkGpioExample"
date: "2016-04-05"
---
Some examples are distributed with Pi4J jar.
One of the simplest is BlinkGpioExample : led1 blinks every 1/2 seconds during 15 seconds  and led2 blinks every seconds but speed up the rate when button is pressed.

## Standalone Simulation Mode
Unlike the first tuto, where we used Ptolemy II ([The Ptolemy Project](http://ptolemy.eecs.berkeley.edu/ptolemyII/index.htm)) as a Computed Simulation Environment to drive our debug session, we will choose the standalone simulation mode.
The standalone simulation mode use an internal and configurable time sequencer. You just have to choose the simulation duration (End Time), the simulation precision(Time Increment) and whether the time must be speed up or slow down.(Time Ratio)

## Debug Configuration

After installing ([see getting started]({{{{ site.baseurl }}/gettingstarted.md}})) and creating your project in eclipse, you have to set up  your debug configuration:

![Debug config]({{ site.baseurl }}/images/2016/DebugConfig.png)

Then Right click on RIL-Simulate and choose new configuration
![New Debug configuration]({{ site.baseurl }}/images/2016/DebugConfig2.png)

### Board configuration
You have now to choose which hardware you want to use.
Even with a single Raspberry Pi board, there is a lot of different configuration.
In this example, GPIO1 and GPIO3 are used as outputs and GPIO2 is an input.

So, click on "Configure Board", in the "Manage Hardware list" click on "Add..."
![manage hardware]({{ site.baseurl }}/images/2016/ManageHardwareLiust.png)

Name your new hardware, check GPIO 1 and 3 as outputs, 2 as input and leave the other unused and save it.
![ Configure board]({{ site.baseurl }}/images/2016/ConfigureBoard.png)



### Standalone settings

Choose stand alone as Simulation Mode and choose
![Standalone]({{ site.baseurl }}/images/2016/DebugConfigStandalone.png)

Then,  "Debug" !!

### Results
The output console should display this :
```
<--Pi4J--> GPIO Blink Example ... started.
 ... the LED will continue blinking until the program is terminated.
 ... PRESS <CTRL-C> TO STOP THE PROGRAM.
2016-03-30 15:38:50 INFO  TimeSequencer:93 - Simulated Time: Duration[60.0 s], StepIncrement[0.001 s], Ratio[0.1]
2016-03-30 15:38:50 INFO  TimeSequencer:137 - Value for GPIO 1 @0,00: true
2016-03-30 15:38:50 INFO  TimeSequencer:137 - Value for GPIO 3 @0,00: true
2016-03-30 15:38:50 INFO  TimeSequencer:137 - Value for GPIO 1 @0,56: false
2016-03-30 15:38:50 INFO  TimeSequencer:137 - Value for GPIO 1 @1,04: true
...
2016-03-30 15:38:51 INFO  TimeSequencer:137 - Value for GPIO 3 @58,44: true
2016-03-30 15:38:51 INFO  TimeSequencer:137 - Value for GPIO 3 @59,92: false
2016-03-30 15:38:51 INFO  Handler:75 - Stop Called
2016-03-30 15:38:51 DEBUG Handler:66 - main was stopped: null
```

You can the change of each output with the number of second since the simulation start and the value of the output.
