---
title: How to program
summary: Basics of programming SBM and SBC
authors:
    - Alexander Kolotov
---
# How to program

This section provides links on the materials describing different aspects of programming Arduino and Raspberry Pi boards.

## Arduino 

Since the Arduino board is a quite mature technology there are lots of materials covering different aspects of developing programs to control peripheral devices connected to the controller.

The development process is trivial: the program are written on a PC or a laptop, compiled and downloaded to the Arudino controller by using a USB cable. Most probably, you will use [Arduino IDE](https://www.arduino.cc/en/Guide) to create programs, so it will perform all the actions described above automatically.

Before attempts to prepare the first sketch (a sketch is the name that Arduino uses for a program) read few advices that could help to become more successful as an Arduino programmer:

  * [Writing code of Arduino devices](http://techgenix.com/writing-code-for-arduino/)
  * [5 tips to improve your Arduino coding skills](https://thekurks.net/blog/2017/12/4/5-tips-to-improve-your-code).

If you had no any experience with Arduino, it makes sense to go through the set of lessons to get basic ideas about this device programming. So, do not hesitate and look at [Arduino lessons](https://learn.adafruit.com/series/learn-arduino).

Different ways to control motors and query sensors has been covered in the section [Electromechanical components](p02-electronics.md) therefore they will not be repeated here. Instead it is necessary to focus on some tips and tricks, and advanced techniques that are used for complex projects.

For example, the portal [The Robotics Back-End](https://roboticsbackend.com/category/arduino/) has the great list of Arduino tutorials. Here you can find [an answer for question whether Arduino is good for industrial projects](https://roboticsbackend.com/is-arduino-used-in-real-life-products/), learn [how to write multitasking applications on Arduino](https://roboticsbackend.com/how-to-do-multitasking-with-arduino/), practise [to create your own Arduino library](https://roboticsbackend.com/arduino-create-library/) and understand techniques [to write realtime software for Arduino](https://roboticsbackend.com/arduino-compute-duration-code-example/).

Eventually, you could be ready to use the Arduino board as a powerful driver. The main controller (Raspberry Pi) will encode and send commands to this driver, it will decode the commands and schedule getting information from sensors or prepare instructions for motors. Consider the following set of useful tutorials and libraries that could help you build control systems based on Arduino:

  * [A library for Non-trivial programing for Arduino](https://www.thecoderscorner.com/products/arduino-libraries/io-abstraction/)
  * [Event-based Programming with Arduino](https://github.com/johnnyb/Eventually)
  * State machines with Arduino:
    * [State machines tutorial](https://github.com/j-bellavance/Tutorials/tree/master/State%20machines%20Tutorial)
    * [Multitasking on the Arduino with a Finite State Machine](https://medium.com/coinmonks/multitasking-on-the-arduino-with-a-finite-state-machine-and-why-youll-need-it-for-sigfox-d52dafc55d8e)
    * Finite State Machine Programming Basics: [part 1](https://arduinoplusplus.wordpress.com/2019/07/06/finite-state-machine-programming-basics-part-1/) and [part 2](https://arduinoplusplus.wordpress.com/2019/07/19/finite-state-machine-programming-basics-part-2/)
    * [A library that implements a basic State Machine](https://github.com/jrullan/StateMachine)

Separately it is necessary to say about [the digital signal processing](https://en.wikipedia.org/wiki/Digital_signal_processing). When you work with digital and analogue sensors, you will definitely meet with the fact that most of these sensors are noisy. In some cases they could have their own noise suppression mechanism but sometimes it is necessary to implement your own approach to handle data received from the sensors.

That's why it makes sense to start learning different ways how to "de-noise" the sensor readings, so take into consideration the following articles:

  * [Three Methods to Filter Noisy Arduino Measurements
](https://www.megunolink.com/articles/coding/3-methods-filter-noisy-arduino-measurements/)
  * [Simple High-pass, Band-pass and Band-stop Filtering](https://www.norwegiancreations.com/2016/03/arduino-tutorial-simple-high-pass-band-pass-and-band-stop-filtering/)
  * [Implementation of Basic Filters](https://elvistkf.wordpress.com/2016/04/19/arduino-implementation-of-filters/)

## Raspberry Pi

One could consider [the Raspberry Pi board](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/) as a usual computer (PC or laptop) -- a general operating system needs to be installed on the device, it must be equipped with a storage to keep files, a keyboard and a display could be connected to a special sockets. This allows every one to experiment with the board before it will be incorporated in a robotics project.

Although Microsoft Windows 10 supports the Raspberry Pi, the common recommendation is to install a Linux-based operating system. Depending on the type of distribution you will choose, low power consumption and high performance could be achieved with a proper configuration. 

So, in order to getting with the board, at first, start with the [installation](https://www.raspberrypi.org/documentation/installation/). Then, especially you did not work before with a Linux systems, take [a tour what is available on the Raspberry Pi](https://projects.raspberrypi.org/en/projects/raspberry-pi-getting-started/5) to be used on daily basis and dig into [Linux essentials](https://www.raspberrypi.org/documentation/linux/) to learn more about commands that could help you to use the system more effectively.

As soon as the first issues were solved and there is an understanding how turn on the board, start using it and gracefully switch off, the next step will be to start programming it. Even if it is possible to program on any language you would like, the most convenient way will be to use Python. This programming languages has low entrance level and have tons of materials in the Internet to begin coding with it. For example, you can try [LearnPython.org](https://www.learnpython.org/).

If the first programming concepts are clear, the logical continuation is to understand how the language can be used to [interact with electronic components](https://realpython.com/python-raspberry-pi/#interacting-with-physical-components).

And, finally, you would like to start using the Raspberry Pi together with a camera. Here it is necessary to say, that the board supports several options to work with camera. First of all, the same as for the general purpose computer, the camera can be plugged into an USB socket. In the python code you need to get access a proper device (usually, `/dev/video0`) and start reading frames from it:

```python
#!/usr/bin/python
import os
import pygame, sys

from pygame.locals import *
import pygame.camera

width = 640
height = 480

#initialise pygame   
pygame.init()
pygame.camera.init()
cam = pygame.camera.Camera("/dev/video0",(width,height))
cam.start()

#setup window
windowSurfaceObj = pygame.display.set_mode((width,height),1,16)
pygame.display.set_caption('Camera')

#take a picture
image = cam.get_image()
cam.stop()

#display the picture
catSurfaceObj = image
windowSurfaceObj.blit(catSurfaceObj,(0,0))
pygame.display.update()

#save picture
pygame.image.save(windowSurfaceObj,'picture.jpg')
```
_The code is taken from [the official forum](https://www.raspberrypi.org/forums/viewtopic.php?p=597987&sid=a060e0e27badaa659d3858cd8ac0ec6c#p597987)_

Another way is to use a specialized Raspberry Pi camera. Since it is connected through a special socket, you can get better results from performance point of view. But from other side, before using the camera's port, it needs to be explicitly turned on in the Raspberry PI Software Configuration tool. You can follow [this tutorial](https://pythonprogramming.net/camera-module-raspberry-pi-tutorials/?completed=/terminal-navigation-raspberry-pi-tutorials/) that help you to check how the Raspberry Pi camera can be programed. 

And now you could be ready to start building a self-driven car around the Raspberry Pi! Don't rush -- consider also an approach to [connect to the board by a Secure Shell terminal through WiFi](https://roboticsbackend.com/enable-ssh-on-raspberry-pi-raspbian/#Enable_ssh_on_Raspberry_Pi_4_without_any_monitor). It will be more convenient to run and stop programs remotely without necessity to have keyboard and monitor plugged into a moving car.

At this moment, you can read a short story (with lots of technical details) how to build [a Vision-Controlled Car Using Raspberry Pi From Scratch](https://heartbeat.fritz.ai/building-a-vision-controlled-car-using-raspberry-pi-from-scratch-1daa042169c6).

Since Python is a general purpose language and the Raspberry Pi board runs a general purpose operating system you can implement any method or use any technique to write a control program for your self-driven car. Definitely the program should not be linear since the robot must act adequately when drive through the track and avoid an obstacle. Adequately means in proper time and without blocking the program to react on other event. So, probably the first step to understand how it can be done is to look at [two ways to handle control loops in Python](https://diyrobocars.com/2017/05/18/two-ways-to-handle-control-loops-in-python/).