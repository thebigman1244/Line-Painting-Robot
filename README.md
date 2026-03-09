Autonomous GPS Field Line Painting Robot
Overview

This project is an autonomous robot designed to paint straight athletic field lines using GPS navigation and compass heading correction. The system is capable of driving between predefined coordinates while maintaining a straight path using a combination of GNSS positioning and heading feedback from a magnetometer.

The robot is powered by an ESP32 microcontroller and uses dual hub motors with independent controllers to achieve differential steering. A built-in WiFi interface allows a user to connect to the robot from a phone or computer and start the robot after placing it at the correct starting position.

The goal of the project was to design and build a practical robotics system that can solve the annoying task of manually painting the lines on a baseball field or sports field in general and also to make it cheaper then a commerical one.


Project Goals

The main goals of this project were to design and build a fully functional autonomous robot and create a system capable of driving in a straight line using sensor feedback.


The project also focuses on building a simple wireless control interface and documenting the entire engineering process from start to finish.

Overall, this project focuses on creating a practical autonomous system while learning the fundamentals of robotics and navigation.

Key Features
Differential Drive System

The robot uses two independent hub motors mounted on either side of the chassis. Each motor has its own motor controller, allowing the robot to steer using differential drive.

This means the robot turns by adjusting the speed of each wheel.

For example:

Both motors running at the same speed allow the robot to drive straight.
If the left motor runs slower, the robot turns left.
If the right motor runs slower, the robot turns right.

This steering method is commonly used in autonomous robots and mobile robotics platforms.

GPS Navigation

The robot uses a GNSS receiver to determine its position on the field.

The GPS system provides latitude, longitude, and satellite data. This allows the robot to measure the distance between its current location and a target coordinate.

Using this information, the robot can determine when it has reached the end of a line.

Compass Heading Control

A magnetometer measures the robot's heading relative to Earth's magnetic field.

This is important because GPS alone cannot keep a robot moving in a perfectly straight direction. The compass provides heading feedback so the robot can correct its steering while driving.

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

Once started, the robot automatically drives toward the target coordinate while correcting its heading using compass feedback.

This approach keeps the system simple while still allowing accurate line placement.

Hardware

The robot is built using the following hardware components.

Microcontroller

The system is controlled by an ESP32.

The ESP32 handles motor control, the web interface, GPS communication, compass heading calculations, and navigation logic.

GNSS Receiver

The robot uses a u-blox ZED-F9P GNSS receiver.

This module provides high quality GNSS positioning data and is capable of centimeter-level accuracy if RTK corrections are added in the future.

Magnetometer

The robot uses a BMM150 3-axis magnetometer.

This sensor measures the Earth's magnetic field and allows the robot to determine its heading.

Motor System

The robot uses two 10-inch hub motors, each controlled by its own motor controller. This setup allows precise speed control and differential steering.

The wheel configuration consists of two rear hub motors and one front caster wheel.

This configuration is commonly used in robotics because it is mechanically simple and easy to control.

Relay Direction Control

Each motor controller includes reverse wires that enable reverse mode when shorted together.

Relays are used to electronically connect these wires, allowing the robot to switch between forward and reverse operation through software control.

Software Architecture

The robot software runs on the ESP32 and is divided into several main systems.

Motor Control

The motor control system handles throttle signals, motor direction control, and steering adjustments.

Navigation System

The navigation system is responsible for reading GPS coordinates, calculating distance to the target, and determining heading corrections.

Sensor Integration

Sensor integration combines data from the GNSS receiver and the magnetometer.

Web Server

The ESP32 runs a lightweight web server that provides the control interface. Users connect directly to the robot's WiFi network and control it through a browser.

Navigation Strategy

The robot follows a simple navigation process.

First, the user places the robot at the correct starting position. The robot checks that it is aligned with the required heading.

Next, the robot begins driving toward the target coordinate.

Compass feedback continuously corrects steering while the robot is driving.

GPS distance measurement determines when the target point has been reached, and the robot stops automatically.

This approach avoids complicated path planning while still allowing accurate autonomous movement.

Parts List

Below is a list of the major components used in this project. Links will be added later.

Electronics

ESP32 development board https://www.amazon.com/ELEGOO-ESP-WROOM-32-Development-Bluetooth-Microcontroller/dp/B0D8T53CQ5/ref=sr_1_3?dib=eyJ2IjoiMSJ9.0mMutUw27FQh3oBplnQp1W-j79c1kFkqAhjtYy2WbRDceGeIFW8zDhzGIBDP64tt_MPF-F7llygbb1i9VdwfIIKkt5EgEM20Jfw_vuUlzLLey0sZQGBEQp_43hHyZ5bB192qxpbnWD3Fn68eelh4dzABZUXRC6oRmted5OnREE1YZqjQOT3pPFXLSTmxjttgHPVNT1Oxc8BO1wZDEpdLBv5816-crY8qR0c4LFmluS8N1K-72KhGUj0eTZGaeiriOLRC1i-SbLIitTckrje_a1Cb64lBdPrPI8xzsd1NDl4.rnB65lNcputYtCMz0BASFEZvZuFks9MasTFjgwToBBI&dib_tag=se&keywords=esp32&qid=1773080585&s=electronics&sr=1-3
u-blox ZED-F9P GNSS receiver https://www.amazon.com/SparkFun-GPS-RTK2-Board-ZED-F9P-Qwiic/dp/B07NBPNWNZ/ref=sr_1_1?crid=3PQ58QY6EN2N5&dib=eyJ2IjoiMSJ9.z1Abcsi_nd3n9YQYycycs2fFeO5Q448aYvtKq_QBcK6yDNsyFRm1wVPd4AyVqHciaSE0upOIkhfzq2q9qx25IO3v85XEoli1vh6OwemL0FsPJIIv-Otn3Kmm8i65uCh6mVL9kqtnvBECML5GfT6Lyskq_Nd3xdJy-LU5v9F_vs8r5fYkVdHNz7n4Gcl7H77bc66CHwjMS-FGq31j3guAk_nDLxoYGMOi3WZN9paK6H7Edff7OYN07gUxBVtY8ATWmcwn3xc2sCknW0dq1KrX5mlkDafgKaQ0BO9YmcSUqNY.5fE7pLzpEsekCYnvj1zfPcVGTAgMYuL2jXAiPC5qcGk&dib_tag=se&keywords=Zed+f9p&qid=1773080674&sprefix=zed+f9p%2Caps%2C168&sr=8-1

BMM150 magnetometer module

2 relay modules for motor reverse control

DC-DC voltage converters

Wiring and connectors

Drive System

Two 10-inch hub motors
Two motor controllers
8-inch caster wheel

Structure

Robot frame
Mounting brackets
Electronics enclosure

Hardware

Water-based paint pump
Spray nozzle system
Paint reservoir

Future Improvements


Adding RTK GPS corrections could improve positioning accuracy from a few feet to a few centimeters.

Improved navigation algorithms could allow the robot to automatically correct its starting alignment.

Future versions may also support custom field mapping instead of only preset coordinates.

Motor ramping and filtering could also be added to create smoother acceleration and steering.

Project Status

The robot currently has working motor control, a functioning WiFi control interface, working GPS communication, and a compass heading system.

Direction control has also been implemented.

The robot is capable of driving and maintaining heading using sensor feedback.

About the Author

This project was created by Bryce Gilmartin, a 14-year-old kid.

The goal of this project was to learn more about robotics, embedded systems, and navigation while building something practical from scratch.

Other interests include astrophotography, telescope systems, and astronomy.

License

This project is open for learning and experimentation. If you reuse or publish this project, please credit this repository.
