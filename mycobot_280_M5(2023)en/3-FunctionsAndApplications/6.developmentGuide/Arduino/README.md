# Arduino

![arduino](../../../resources\3-FunctionsAndApplications\6.developmentGuide\Arduino/ard-01.jpg)

## What is Arduino?

**Arduino** is an easy-to-use, easy-to-use open source electronic prototyping platform, which includes hardware (various development boards that meet Arduino specifications) and software (Arduino IDE and related development kits).
The hardware part (or development board) consists of a microcontroller (MCU), flash memory (Flash) and a set of general input/output interfaces (GPIO), etc. You can think of it as a microcomputer motherboard.
The software part mainly consists of the PC-side Arduino IDE and related board support packages (BSP) and rich third-party function libraries. Users can easily download the BSP and required function libraries related to the development board you have through Arduino IDE to write your program.

## What can MyCobotBasic library do?
MyCobotBasic library is an open source robot control library developed by our company. It can only be used with robots developed by our company. With this library, you can control our robots through Bluetooth, WiFi, serial ports, etc., and it also supports external sensors, IIC communication, LED lights and other functions. You can DIY different application scenarios according to your needs, or refer to the MiniRobot sample code or angle, coordinate, gripper and other control cases we provide. The MiniRobot sample code contains control-related content such as Bluetooth, WiFi, drag teaching, and distance sensors.

**Applicable devices:**

- myCobot 280
- myCobot 280 M5

**Prerequisites:**

- **M5** series version, **M5Stack-basic** burn **miniRobot** at the bottom, select **Transponder** function, **ATOM** burn the latest version of **atomMain** at the end (factory default burned)

## Arduino development guide

You can use it according to the following instructions Arduino develops our robotic arm
1. [Environment setup](./10.1-arduino_download.md)

2. [Simple use](./10.2-arduino_use.md)

3. [API description](./10.3-api.md)