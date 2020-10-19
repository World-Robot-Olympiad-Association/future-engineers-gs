---
title: How to program
summary: Basics of programming SBM and SBC
authors:
    - Alexander Kolotov
---
# How to program

This section provides links on the materials describing different aspects of programming Arduino and Raspberry Pi boards.

## Arduino 

Since the Arduino board is quite mature technology there are lots of materials covering different aspects of developing programs to control peripheral devices connected to the controller.

The development process is trivial: the program are written on a PC or a laptop, compiled and downloaded to the Arudino controller by using a USB cable. Most probably, you will use [Arduino IDE](https://www.arduino.cc/en/Guide) to create programs, so it will perform all the actions described above automatically.

Before attempts to prepare the first sketch (a sketch is the name that Arduino uses for a program) read few advices that could help to become more successful as an Arduino programmer:

  * [Writing code of Arduino devices](http://techgenix.com/writing-code-for-arduino/)
  * [5 tips to improve your Arduino coding skills](https://thekurks.net/blog/2017/12/4/5-tips-to-improve-your-code).

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

TBD