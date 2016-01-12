---
layout: post
title: BlinkGpioExample
---
Distributed with Pi4J jar, you will find some examples.
One of the simplest is BlinkGpioExample : led1 blinks every 1/2 seconds uring 15 seconds  and led2 blinks every seconds but speed up the rate when button is pressed.

## Ptolemy Project
We will use Ptolemy II ([The Ptolemy Projecy](http://ptolemy.eecs.berkeley.edu/ptolemyII/index.htm)) as Computed Simulation Environment. This was the first (and currently the only one) tool I have tested with FMU co-simulation. Meanwhile, the FMI standard publish a compatibility table showing which tool is able to use FMU in master co-simulation.

Download and install Ptolemy II

Then Download the sample Ptolemy Project : [www.raspinloop.org/data/Ptolemy_blinkGpioExample.xml]({{ site.baseurl }}/data/Ptolemy_blinkGpioExample.xml) and open it in Ptolemy:

![ptolemy start]({{ site.baseurl }}/images/ptolemystart.png)

`file -> Open File` and select the previously downloaded `Ptolemy_blinkGpioExample.xml`

![ptolemy project opened]({{ site.baseurl }}/images/ptolemyprojectopened.png)

The project consists of 4 different parts:

* The Director
* Input signal generation
* The FMU binding
* Output Visualization

### The Director
Ptolemy II is based on a class of models called actor-oriented models , or more simply, actor models.
Actors are components that execute concurrently and share data with each other by sending messages via ports.

The director is responsible to coordonate dataflow through port of each block. Continuous director is able to computes in each iteration, a fixed point for all signal values. In each iteration, time is advanced by an amount determined by the solver. (see [Ptolemy getting started](http://ptolemy.eecs.berkeley.edu/books/Systems/chapters/IGettingStarting.pdf))

Our configuration for the Step size is : 

`stopTime : 30` The simulation stops after 30 seconds

`initStepSize : 0.005`

`maxStepSize : 0.005`

So, each iteration will represent 0.005 seconds. An interresting parameter could be `synchronize to realtime`. With this option each iteration will occurs evrey 0.005 second instead of 'as soon as possible'.

### Input signal generation
On the left part of the schema, we put a Squarewave generator to simulate the button signal. This was done with a sinewave generator and a comparator to set a signal to *true* when sinus is positive and *false* otherwise.

TriggeredSinewave is configured like this: 

`frequency : 0.1` 0.1 Hertz means positive for 5 seconds positive and negative for the other 5 seconds...


### The FMU binding

This is the *Main* block. This block is the FMU (functional mockup unit) of Raspberry Pi. It will behave like all other blocks, with their inputs and output. Expect that , this block will communicate with Eclipse to allow the java application to read inputs ans set outputs.

To configure it, we have to download the Raspberry_b.fmu (currently only the B model)  [www.raspinloop.org/data/fmu/raspberry_b.fmu](www.raspinloop.org/data/fmu/raspberry_b.fmu) then import it in Ptolemy:

![ptolemy import fmu]({{ site.baseurl }}/images/ptolemyimportfmu.png)

*DO NOT CHECK : Import for model exchange*
![ptolemy import path]({{ site.baseurl }}/images/ptolemyimportpath.png)

As explained in the warning, the imported actor as a lot of variables, it is up to us to select which of them we want to see as port.
So `Select FMU -> right click -> Customize -> Port`

![ptolemy FMU port]({{ site.baseurl }}/images/ptolemyfmuports.png)

We have to _uncheck ALL outputs except GPIO1, GPIO3_ which should be visible (uncheck hidden) and to _uncheck ALL inputs except GPIO2_i_ which should also be visible.

We may 'wire' GPIO2_i to the wire outgoing from Squarewave generator.

### Output Visualization

In order to view the output, we use a block called timePlotter. This block doesn't accept boolean as input, so we have to add a BooleanToAnything converter between FMU output and the plotter.

Now you may 'wire' your output to the converters

*Note:* You have to add another conveter to be able to wire the GPIO3. (try crtl-c -> ctrl-v)


You should have something like that....
![ptolemy wired]({{ site.baseurl }}/images/ptolemywired.png)


## RUN !

Now , we have to start your project in eclipse debugger [(see install)]({{ site.baseurl }}/Install/), wait for the message `INFO  [Server] Starting the simple server...` and Run the model in ptolemy.

I hope you 'll feel the same exaltation as me seeing this graph.

![ptolemy grap]({{ site.baseurl }}/images/ptolemyresults.png)

Pens:

* red: the input to GPIO02
* blue: the GPIO1 output (led1 // continuously blink the led every 1/2 second for 15 seconds)
* cyan: the GPIO3 output (led2 // continuously blink the led every 1 second except when button is pressed -> speed up the blink rate)

