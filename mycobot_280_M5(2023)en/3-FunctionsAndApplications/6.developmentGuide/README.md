# Chapter 6 Software Development Guide

## Usage Environment

mycobot280 M5 is developed and used based on PC. Since there is no built-in system in the robot arm, the robot arm and PC need to be combined during use. Please prepare the PC before use.

## Development Environment

In order to meet the diverse application needs of robots in different scenarios, we have adapted the robot to multiple programming languages. So far, we have adapted the following mainstream programming languages, and we think you can use any of the following languages ​​for development. Please be sure to follow the instructions strictly. Any omitted steps may cause the corresponding language to fail to run successfully. I wish you a smooth use of the robot.<br>

[6.1 Python](python/README.md)<br>
Our robot supports Python, and the development of the Python API library is also becoming more and more perfect. The robot's joint angles, coordinates, grippers and other aspects can be controlled by Python. <br>

[6.2 ROS1](ROS/12.1-ROS1/12.1.1-Introduction.md)<br>
ROS (Robot Operating System), as an open source robot operating system, provides unlimited possibilities for robot development and control. Our robot can be controlled in a modular way through ROS's rich control functions. Whether it is joint control, path planning or sensor feedback, ROS provides corresponding tools and libraries to make the control process more flexible and efficient. </br>

[6.3 ROS2](ROS/12.2-ROS2/12.2.3-ROS2Introduction.md)<br>
ROS 2 (Robot Operating System 2) is a flexible software framework designed for robot software development. Our robot can make application development more efficient and modular through a series of services and functions such as hardware abstraction, device drivers, library functions, visualization tools, messaging, and package management. </br>
[6.4 Communication](CommunicationProtocolPackage/18-communication.md)<br>
If you have a certain understanding of information theory, coding and robot communication functions, then you should understand that all communication originates from data transmission. In order to facilitate users to operate the robot, we have opened a communication protocol based on serial communication. You can use the serial assistant or encapsulate it into any programming language you are familiar with to control the robot.<br>
[6.5 Arduino](Arduino/README.md)<br>
Arduino is an easy-to-use and easy-to-use open source electronic prototyping platform. Users can use the Arduino IDE to easily download the BSP and required function libraries related to the development board you have to write your program. The MyCobotBasic library is an Arduino open source robot control library developed by our company. This library can be used to control our robots through Bluetooth, WiFi, serial ports, etc.<br>
[6.6 Blockly](myBlocklyAndUlFlow/README.md)<br>
myBlockly is a puzzle-style programming software developed by the R&D team of Shenzhen Elephant Robot Company. It is based on the python environment and the pymycobot dependency library, allowing users to program and control the mycobot robot in a building block-like manner.<br>
[6.7 C++](Cplus/README.md)<br>
C++ is the inheritance of C language. It can be used for both procedural programming in C language and object-based programming characterized by abstract data types. Using C++ language, you can freely develop (coordinate control, angle control, io control, gripper control, etc.) through the C++ dynamic library developed by our company, and control some robots that our company has developed.<br>
[6.8 C#](Csharp/README.md)<br>
C# is an object-oriented programming language derived from C and C++ released by Microsoft, and a high-level programming language that runs on .NET Framework and .NET Core (completely open source, cross-platform). Using the C# language, you can freely develop (coordinate control, angle control, io control, gripper control, etc.) through the C# dynamic library provided by our company, and control some robots that our company has developed.<br>
[6.9 JavaScript]( JavaScript/README.md)<br>
JavaScript is a scripting language that runs on the client; it does not need to be compiled, and the js interpreter interprets and executes each one during the running process. Our company's robots support development using JavaScript.

---

[← Previous Chapter](../5.BasicFunction/README.md) | [Next Chapter →](../7.SuccessfulCase/7-SuccessfulCases.md)