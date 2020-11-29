---
title: How to program
summary: Basics of SBM and SBC programming
authors:
    - Alexander Kolotov
---
# How to program

This section provides links to materials describing different aspects of programming Arduino and Raspberry Pi boards.

## Arduino 

Since the Arduino board is a mature technology, there are lots of materials covering different aspects of developing programs to control peripheral devices connected to the controller.

The development process is simple: the programs are written on a PC or a laptop, them compiled and downloaded to the Arudino controller by using a USB cable. Most likely, you will use [Arduino IDE](https://www.arduino.cc/en/Guide){target=_blank} to create programs, so it will perform all the actions described above automatically.

Before you attempt to prepare the first sketch (a sketch is the name that Arduino uses for a program) read few articles that could help you become more successful as an Arduino programmer:

  * [Writing code for Arduino devices](http://techgenix.com/writing-code-for-arduino/){target=_blank}.
  * [5 tips to improve your Arduino coding skills](https://thekurks.net/blog/2017/12/4/5-tips-to-improve-your-code){target=_blank}.

If you have not had any experience with Arduino, it makes sense to go through a set of lessons to get basic concepts about programming this device. So do not hesitate to look at [Arduino lessons](https://learn.adafruit.com/series/learn-arduino){target=_blank}.

Different ways to control motors and query sensors are covered in the section [Electromechanical components](p02-electronics.md), therefore they will not be repeated here. Instead, it is necessary to focus on some tips and tricks and advanced techniques that are used for complex projects.

For example, the portal [The Robotics Back-End](https://roboticsbackend.com/category/arduino/){target=_blank} has a great list of Arduino tutorials. Here you can find [an answer for the question of whether Arduino is good for industrial projects](https://roboticsbackend.com/is-arduino-used-in-real-life-products/){target=_blank}, learn [how to write multitasking applications on Arduino](https://roboticsbackend.com/how-to-do-multitasking-with-arduino/){target=_blank}, practise [to create your own Arduino library](https://roboticsbackend.com/arduino-create-library/){target=_blank} and understand techniques [to write realtime software for Arduino](https://roboticsbackend.com/arduino-compute-duration-code-example/){target=_blank}.

Eventually, you will be ready to use the Arduino board as a powerful driver. The main controller (Raspberry Pi) will encode and send commands to this driver. It will decode the commands and schedule retrieving information from sensors or prepare instructions for motors. Consider the following set of useful tutorials and libraries that could help you build control systems based on Arduino:

  * [A library for Non-trivial programing for Arduino](https://www.thecoderscorner.com/products/arduino-libraries/io-abstraction/){target=_blank}
  * [Event-based Programming with Arduino](https://github.com/johnnyb/Eventually){target=_blank}
  * State machines with Arduino:
    * [State machines tutorial](https://github.com/j-bellavance/Tutorials/tree/master/State%20machines%20Tutorial){target=_blank}
    * [Multitasking on the Arduino with a Finite State Machine](https://medium.com/coinmonks/multitasking-on-the-arduino-with-a-finite-state-machine-and-why-youll-need-it-for-sigfox-d52dafc55d8e){target=_blank}
    * Finite State Machine Programming Basics: [part 1](https://arduinoplusplus.wordpress.com/2019/07/06/finite-state-machine-programming-basics-part-1/) and [part 2](https://arduinoplusplus.wordpress.com/2019/07/19/finite-state-machine-programming-basics-part-2/){target=_blank}
    * [A library that implements a basic State Machine](https://github.com/jrullan/StateMachine){target=_blank}

It is also necessary to mention [the digital signal processing](https://en.wikipedia.org/wiki/Digital_signal_processing){target=_blank}. When you work with digital and analogue sensors, you will definitely discover the fact that most of these sensors are noisy. In some cases, they could have their own noise suppression mechanism, but sometimes it is necessary to implement your own approach to handle data received from the sensors.

That's why it makes sense to start learning different ways to "de-noise" the sensor readings. So take into consideration the following articles:

  * [Three Methods to Filter Noisy Arduino Measurements
](https://www.megunolink.com/articles/coding/3-methods-filter-noisy-arduino-measurements/){target=_blank}
  * [Simple High-pass, Band-pass and Band-stop Filtering](https://www.norwegiancreations.com/2016/03/arduino-tutorial-simple-high-pass-band-pass-and-band-stop-filtering/){target=_blank}
  * [Implementation of Basic Filters](https://elvistkf.wordpress.com/2016/04/19/arduino-implementation-of-filters/){target=_blank}

## Raspberry Pi

One could consider [the Raspberry Pi board](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/){target=_blank} as a usual computer (PC or laptop) -- a general operating system needs to be installed on the device, it must be equipped with storage to keep files, a keyboard and a display could be connected to special sockets. This allows you to experiment with the board before it is incorporated into a robotics project.

Although Microsoft Windows 10 supports the Raspberry Pi, the common recommendation is to install a Linux-based operating system. Depending on the type of distribution you choose, low power consumption and high performance can be achieved with a proper configuration. 

In order to interact with the board, first start with the [installation](https://www.raspberrypi.org/documentation/installation/){target=_blank}. Then, especially if you have not worked with a Linux operating system before, take [a tour what is available on the Raspberry Pi](https://projects.raspberrypi.org/en/projects/raspberry-pi-getting-started/5){target=_blank} for use on a daily basis, and dig into [Linux essentials](https://www.raspberrypi.org/documentation/linux/){target=_blank} to learn more about commands that could help you use the system more effectively.

As soon as the first lessons are complete and you have an understanding of how turn on the board, start using it, and gracefully switch off, the next step will be to start programming it. Even if it is possible to program in any language you would like, the most convenient way will be to use Python. This programming language has a low entrance level and has tons of materials on the Internet to begin coding with it. For example, you can try [LearnPython.org](https://www.learnpython.org/){target=_blank}.

If the first programming concepts are clear, the logical continuation is to understand how the language can be used to [interact with electronic components](https://realpython.com/python-raspberry-pi/#interacting-with-physical-components){target=_blank}.

And, finally, you would like to start using the Raspberry Pi together with a camera. The Raspberry Pi board supports several options to work with camera. First, as with the general purpose computer, the camera can be plugged into a USB socket. In the python code, you need to get access to a proper device (usually, `/dev/video0`) and start reading frames from it:

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

Another way is to use a specialized Raspberry Pi camera. Since it is connected through a special socket, you can get better results from a performance point of view. On the other hand, before using the camera's port, it needs to be explicitly turned on in the Raspberry PI Software Configuration tool. You can follow [this tutorial](https://pythonprogramming.net/camera-module-raspberry-pi-tutorials/?completed=/terminal-navigation-raspberry-pi-tutorials/){target=_blank} that helps you learn how the Raspberry Pi camera can be programmed. 

And now you could be ready to start building a self-driven car around the Raspberry Pi! Don't rush -- consider an approach to [connect to the board by a Secure Shell terminal through WiFi](https://roboticsbackend.com/enable-ssh-on-raspberry-pi-raspbian/#Enable_ssh_on_Raspberry_Pi_4_without_any_monitor){target=_blank}. It will be more convenient to run and stop programs remotely without the necessity of having a keyboard and monitor plugged into a moving car. [Another article](https://www.tomshardware.com/reviews/raspberry-pi-headless-setup-how-to,6028.html){target=_blank} could be useful for more advanced users -- it sheds light on other aspects of communicating to the Raspberry PI board by using a network connection.

Take a moment to read a short story (with lots of technical details) on how to build [a Vision-Controlled Car Using Raspberry Pi From Scratch](https://heartbeat.fritz.ai/building-a-vision-controlled-car-using-raspberry-pi-from-scratch-1daa042169c6){target=_blank}.

Since Python is a general purpose language and the Raspberry Pi board runs a general purpose operating system, you can implement any method or use any technique to write a control program for your self-driven car. Definitely, the program should not be linear, since the robot must act adequately when driving through the track and avoiding an obstacle. Adequately means in proper time and without preventing the program from reacting to other events. The first step to understand how it can be done is to look at [two ways to handle control loops in Python](https://diyrobocars.com/2017/05/18/two-ways-to-handle-control-loops-in-python/){target=_blank}.