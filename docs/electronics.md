---
title: Electronics 
summary: Electromechanical components, controllers and optics
authors:
    - Alexander Kolotov
---
# Electromechanical components

Here is materials that aimed to help understand how to make the vehicle is smarter than an RC toy.

## Design leading questions

Definitely, the obstacles detection and decision making for the motion planning must be done ad-hoc by en electronic brain rather than by a human being. That's why it is needed to choose the set of controllers, electronic components and design the logic to connect them to each other. They will mostly rely on the way how the vehicle will solve the task. But some ideas will be common due to the nature of the challenge.

Here is the set of questions that is intended to boost the process of thinking about electronic filling of the autonomous car:

  1. Will a camera be used to recognize the traffic signs (red and green pillars)? Is it an USB-camera or a natively plugged device (like the Raspberry Pi camera)?

  2. How fast the video stream from the camera must be handled? What is suitable performance of the decision making controller?
  
  3. Will the vehicle be controlled by one controller or by a pair of the main controller and an auxiliary controller? How will the roles between controllers be distributed: handling of the video stream, direct control of the motors, direct acquiring of sensors readings? Will capacity (input/output pins) of each controller be enough for this? What kind of connection will be between the controllers? 
  
  4. Will the walls be detected by camera or by a distance/proximity sensors?
  
  5. Should a special lens kit be used to make the camera's field of view wider to recognize both traffic signs and walls or several cameras will be used instead?
  
  6. How will the passed path be measured: by counting numbers of turns with a compass or a gyroscope, by calculating the distance with an encoder(s), by detecting colored lines with light sensors? 
  
  7. Will a gyroscope and/or an accelerometer be used to assist in accurate driving -- get rid of excessive steering mechanism shifts?
  
  8. What kind of power sources should be used to supply controllers, motors and senors? Should it be one source for all consumers or dedicated sources for controllers and motors?