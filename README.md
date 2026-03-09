Autonomous GPS Field Line Painting Robot
Overview

This project is an autonomous robot designed to paint straight athletic field lines using GPS navigation and compass heading correction. The system is capable of driving between predefined coordinates while maintaining a straight path using a combination of GNSS positioning and heading feedback from a magnetometer.

The robot is powered by an ESP32 microcontroller and uses dual hub motors with independent controllers to achieve differential steering. A built-in WiFi interface allows a user to connect to the robot from a phone or computer and start the robot after placing it at the correct starting position.

The goal of the project was to design and build a practical robotics system that can solve the annoying task of manually painting the lines on a baseball field or sports field in general and also to make it cheaper then a commerical one.


Project Goals

The main goals of this project were to design and build a fully functional autonomous robot and create a system capable of driving in a straight line using sensor feedback. And to also make a robot for less than $2000.


Key Features
Differential Drive System

The robot uses two independent hub motors mounted on either side of the chassis. Each motor has its own motor controller, allowing the robot to steer using differential drive.

This means the robot turns by adjusting the speed of each wheel.

For example:

Both motors running at the same speed allow the robot to drive straight.
If the left motor runs slower, the robot turns left.
If the right motor runs slower, the robot turns right.


GPS Navigation

The robot uses a GNSS receiver to determine its position on the field.

The GPS system provides latitude, longitude, and satellite data. This allows the robot to measure the distance between its current location and a target coordinate.

Using this information, the robot can determine when it has reached the end of a line.

If you feel accuracy lacks then you can add a RTK station which means buying a second Zed-F9P and with having a second one it helps over come atmospheric distortion and radio frequency distruption which therefor allows more accurate starting postion of the robot.


Compass Heading Control

A magnetometer measures the robot's heading so it can have real time corrections incase of drift.

This is important because GPS alone cannot keep a robot moving in a perfectly straight direction. 

The navigation correction loop works as follows:

The robot calculates the desired heading to the target point.
The compass measures the current heading.
If the robot drifts left or right, motor speeds are adjusted to correct the direction.

This allows the robot to maintain a straight path while driving.

Web Interface Control

The robot creates its own WiFi network using the ESP32.

A phone or computer can connect directly to the robot and open a control interface in a web browser.

The interface allows the user to drive the robot manually, start autonomous line programs, and stop the robot.

This makes it easy to operate the robot without installing any additional software.

Preset Line Paths

Instead of manually driving the robot during operation, the system uses predefined start and end coordinates.

The operator places the robot at the correct starting position and aligns it with the required heading.

Once started, the robot automatically drives toward the target coordinate while correcting its heading using compass feedback. And automatically reverse back to the starting point.


Hardware

The robot is built using the following hardware components.

ESP 32

ZED-F9P GNSS Reciever

BMM150 Magnetometer

Dual 800W Motor System

The robot uses two 10-inch hub motors, each controlled by its own motor controller. This setup allows precise speed control and differential steering.

One straight mounted castor wheel.

Relay Direction Control

Each motor controller includes reverse wires that enable reverse mode when shorted together.

Motor Control

The motor control system handles throttle signals, motor direction control, and steering adjustments.

Navigation System

The navigation system is responsible for reading GPS coordinates, calculating distance to the target, and determining heading corrections.

Sensor Integration

Sensor integration combines data from the GNSS receiver and the magnetometer.

Web Server

The ESP32 runs a lightweight web server that provides the control interface. Users connect directly to the robot's WiFi network and control it through a browser. Another added feature is a QR code which is below and when one connects to the robots AP then they must scan a qr code which send a request to the robot and it alows them to easily get to the website.

Navigation Strategy

The robot follows a simple navigation process.

First, the user places the robot at the correct starting position. The robot checks that it is aligned with the required heading.

Next, the robot begins driving toward the target coordinate.

Compass feedback continuously corrects steering while the robot is driving.

GPS distance measurement determines when the target point has been reached, and the robot stops automatically.

And after it reverses back to the starting point and has to be manually flipped around.

Parts List

Below is a list of the major components used in this project. Links will be added later.

Electronics

ESP32 development board 

u-blox ZED-F9P GNSS receiver 

BMM150 magnetometer module

2 relay modules for motor reverse control

48-12V Converter for the pump
48-5V Converter with USB-C output for ESP32 power
48V Battery with a amperage of >45A


Wiring and connectors

Drive System

Two 10-inch hub motors
Two motor controllers
8-inch caster wheel

Structure

2 long steel beams, and 2 shorter steel beams
Mounting brackets
Electronics enclosure

Hardware

Water-based paint pump
Spray nozzle system
Paint reservoir
Optionial 3D printer in order to print an enclosure for the smaller electronics
Optional sheet plastic to cover all the other electronics

Future Improvements


Adding RTK GPS corrections could improve positioning accuracy from a few feet to a few centimeters.

Future versions may also support custom field mapping instead of only preset coordinates.

Motor ramping and filtering could also be added to create smoother acceleration and steering.

Project Status

The robot currently has working motor control, a functioning WiFi control interface, working GPS communication, and a compass heading system.

The only thing left to add is the pump sprayer, and the code for the actual thing to work.

About the Author

This project was created by Bryce Gilmartin, a 14-year-old kid.

Other interests include astrophotography, telescope systems, and astronomy.

License

This project is open for learning and experimentation. If you reuse or publish this project, please credit this repository or the author.
