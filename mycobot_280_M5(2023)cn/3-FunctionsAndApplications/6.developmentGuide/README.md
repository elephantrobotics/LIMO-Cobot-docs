# 第六章 软件开发指南

## 1 使用环境

mycobot280 M5 是基于 PC 开发和使用的。由于机械臂内没有内置系统，因此在使用过程中需要机械臂和 PC 相结合。使用前请先准备好 PC。

## 2 开发环境

为了满足机器人在不同场景下的多样化应用需求，我们对机器人进行了多种编程语言的适配。到目前为止，我们已经适配了以下主流编程语言，我们认为您可以使用以下任何一种语言进行开发。请务必严格按照说明进行操作。任何遗漏的步骤都可能导致相应语言无法成功运行。祝您顺利使用机器人。

- [6.1 Python](./python/README.md)<br>
  我们的机器人支持 Python，Python API 库的开发也日趋完善。机器人的关节角度、坐标、抓手和其他方面都可以通过 Python 进行控制。<br>

- [6.2 ROS1](ROS/12.1-ROS1/12.1.1-Introduction.md)<br>ROS（Robot Operating System）作为一个开源的机器人操作系统，为机器人的开发和控制提供了无限的可能性。我们的机器人可以通过ROS丰富的控制功能，通过模块化的方式对机器人进行控制。无论是关节控制、路径规划还是感知反馈，ROS都提供了相应的工具和库，使得控制过程更加灵活和高效。</br>
- [6.3 ROS2](ROS/12.2-ROS2/12.2.3-ROS2Introduction.md)<br>
  ROS 2（Robot Operating System 2）是一个灵活的软件框架，专为机器人软件开发而设计。我们的机器人可以通过它提供的硬件抽象、设备驱动、库函数、可视化工具、消息传递以及包管理等一系列服务和功能，使得应用程序的开发变得更为高效和模块化。</br>
- [6.4 Communication](./CommunicationProtocolPackage/18-communication.md)<br>
  如果您对信息论、编码和机器人通信功能有一定的了解，那么您就应该明白，所有的通信都源于数据传输。为了方便用户操作机器人，我们开放了基于串口通信的通信协议。您可以使用串口助手或将其封装到您熟悉的任何编程语言中来控制机器人。
- [6.5 Arduino](./Arduino/README.md)<br>
  Arduino 是一款简单易用、便于上手的开源电子原型平台，使用者可以借由 Arduino IDE 轻松地下载你所持有的开发板相关的BSP和需要的函数库，用于编写你的程序。MyCobotBasic库是我们公司开发的一款 Arduino开源机器人控制库，使用该库可以通过蓝牙、WiFi、串口等方式控制我们的机器人。
- [6.6 Blockly](myBlocklyAndUlFlow/myblocklyTutorials/README.md)<br>
  myBlockly是一款由深圳市大象机器人公司研发团队开发完成的，基于python环境以及pymycobot依赖库的拼图式编程软件，可以让用户以搭积木式的方法进行编程控制mycobot机器人。
- [6.7 C++](./Cplus/README.md)<br>
  C++是C语言的继承，既可以进行C语言的过程化程序设计，又可以进行以抽象数据类型为特点的基于对象的程序设计。使用c++语言，您可以通过我们公司开发的c++动态库，进行自由开发（坐标控制、角度控制、io控制、夹爪控制等），控制我们公司已经研发出来的部分机器人。
- [6.8 C#](./Csharp/README.md)<br>
  C#是微软公司发布的一种由C和C++衍生出来的面向对象的编程语言、运行于.NET Framework和.NET Core(完全开源，跨平台)之上的高级程序设计语言。使用c#语言，您可以通过我们公司提供的c#动态库，进行自由开发(坐标控制、角度控制、io控制、夹爪控制等），控制我们公司已经研发出来的部分机器人。
- [6.9 JavaScript](./ JavaScript/README.md)<br>
  JavaScript是一种运行在客户端的脚本语言；不需要编译，运行过程中由js解释器逐个进行解释并执行。我们公司的机器人支持使用 JavaScript进行开发。

---

[← 上一章](../5.BasicFunction/README.md) | [下一章 →](../7.SuccessfulCase/7-SuccessfulCases.md)