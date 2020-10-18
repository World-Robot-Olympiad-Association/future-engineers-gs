# Hardware

**Materials to help with assembling the vehicle (mechanics and electronics)**

Even if the game rules of the Future Engineering competition does not require to build your own vehicle and allow to use a base of an RC (remote controlled) toy cars, someone would find useful to design everything from very beginning. It will allow to get grain control over the hardware, increase efficiency and reduce errors introduced by the third party's implementations.

The design of the vehicle is dictated by the approach is chosen to drive the rear wheels and implement the steering mechanics. Usually, in the most simple case the rear wheels are fixed on the same axle and rotated by one DC motor. The steering mechanism on the front axle could be build in several ways (https://en.wikipedia.org/wiki/Steering) where the main idea is to change of the angle of the front wheels direction.

Since these concepts are already widely implemented in the RC toy cars and the RC sport vehicles, it makes sense to make a research through available materials. 

The links on the YouTube videos below presents how to build a RC cars from scratch:

* https://youtu.be/ZdtPTUsrAA4
* https://youtu.be/NjAQMPVhdBk
* https://youtu.be/ePDCRdfabZo
* https://youtu.be/CsdP2IEyl2g
* https://youtu.be/NL5-FV28uRA
* https://youtu.be/12CiZusgZng
* https://youtu.be/8JMM5NwO34I
* https://youtu.be/5rJYZLX6uY4
* https://youtu.be/x_3DDoNCBQk
* https://youtu.be/2QUsQxnrYEs
* https://youtu.be/d73MOvDyg38

When you get a basic understanding how your vehicle could look like, you can look at the following instructions that could help to think of the assembling process in more professional manner:

* https://www.sunfounder.com/learn/download/U21hcnRfVmlkZW9fQ2FyX2Zvcl9SYXNwYmVycnlfUGkucGRm/dispi

Note, that some instructions above uses two motors to rotate the rear wheels. In some cases it will make the control of the vehicle more complex since the motors could rotate asynchronously that needs to be compensated by the steering.

By the way, during experiments you can find that the tires in the vehicle have no enough friction with the field surface, so it make sense to consider to try to prepare your own tires for wheels.

* https://youtu.be/LzBm1Zx5Yh0
* https://youtu.be/46OBeW3G7P0
* https://youtu.be/osXwKpGBv5o
* https://youtu.be/nVW-rq43TL0
* https://youtu.be/H5fuGsts6ho
* https://youtu.be/f_aZFameRrc
* https://youtu.be/riSE5syoPWY
* https://youtu.be/i8tiClthnEY
* https://youtu.be/3aI9cHntjdw
* https://youtu.be/ZwFOcSzwNsk

Now is the time to investigate how to make the vehicle is smarter than an RC toy. Definitely, the obstacles detection and decision making for the motion planning must be done ad-hoc by en electronic brain rather than by a human being. That's why it is needed to choose the set of controllers, electronic components and design the logic to connect them to each other. They will mostly rely on the way how the vehicle will solve the task. But some ideas will be common due to the nature of the challenge.

Here is the set of questions that is intended to boost the process of thinking about electronic filling of the autonomous car:

1. Will a camera be used to recognize the traffic signs (red and green pillars)? Is it an USB-camera or a natively plugged device (like the Raspberry Pi camera)?
2. How fast the video stream from the camera must be handled? What is suitable performance of the decision making controller?
3. Will the vehicle be controlled by one controller or by a pair of the main controller and an auxiliary controller? How will the roles between controllers be distributed: handling of the video stream, direct control of the motors, direct acquiring of sensors readings? Will capacity (input/output pins) of each controller be enough for this? What kind of connection will be between the controllers? 
4. Will the walls be detected by camera or by a distance/proximity sensors?
5. Should a special lens kit be used to make the camera's field of view wider to recognize both traffic signs and walls or several cameras will be used instead?
6. How will the passed path be measured: by counting numbers of turns with a compass or a gyroscope, by calculating the distance with an encoder(s), by detecting colored lines with light sensors? 
7. Will a gyroscope and/or an accelerometer be used to assist in accurate driving -- get rid of excessive steering mechanism shifts?
8. What kind of power sources should be used to supply controllers, motors and senors? Should it be one source for all consumers or dedicated sources for controllers and motors?