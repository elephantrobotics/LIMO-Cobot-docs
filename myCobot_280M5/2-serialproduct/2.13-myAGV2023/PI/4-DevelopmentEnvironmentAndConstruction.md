# Development environment and construction

## 1 Introduction to Ubuntu MATE 20.04 system.

**What is Ubuntu?**

Ubuntu is the most widely used Linux operating system in the personal desktop environment. It's a great choice for beginners who want to get familiar with the Linux environment or some embedded hardware operating systems. The Ubuntu official website also offers a dedicated operating system for Raspberry Pi.

![Ubuntu20.04](../../../resourse/20-myAgv2023/PI/Ubuntu20.04.png)

### 1.1 Basic System Function Introduction

#### 1.1.1 The difference between a system and a formal release version.

**Compared to the official version, we have made the following changes:**

- Integration of Python/Ros1/Ros2 and other environments, allowing users to directly use the built-in software provided by our company without the need to set up additional environments.
- Our operating software (myStudio, myBlockly) is pre-installed, eliminating the need for manual installation.
- The system has its own hotspot upon startup (Hotspot Name: ElephantRobotics_AP). You can remotely connect to the system using the VNC remote connection tool without the need for a physical display connection.

#### 1.1.2 Basic System Function Introduction

**Because myAGV Raspberry Pi 2023 version comes with a built-in development environment, the software introduced below can be used directly.**

##### Desktop

![Ubuntu1](../../../resourse/20-myAgv2023/PI/Ubuntu1.png)

1. Test tools to check the proper functioning of myCobot
2. myStudio: It can flash firmware onto the robotic arm
3. myBlockly: Visual modular programming software
4. Ros1/Ros2: A highly flexible software architecture for writing robot software programs
5. Browser and link: You can navigate to our official website and Gitbook (internet connection required)."

##### Toolbar

![Ubuntu13](../../../resourse/20-myAgv2023/PI/Ubuntu13.png)

1. Terminal: Command-line interface
2. File Manager: Used to view the system's storage resources
3. Notepad: Also used to open some script files and view code
4. Vim: Text editor. For more detailed information, please refer to [introduction](https://zh.wikipedia.org/zh-hans/Vim)
5. Show Desktop: Click to directly show the desktop
6. Used to view CPU usage and memory usage
7. Recycle Bin: It is used to store temporarily deleted documents by the user and can restore files stored in the Recycle Bin.

##### Built-in Software

###### myStudio

- Firmware flashing and updates
- Provides tutorial materials, such as user manuals and tutorial videos
- Offers maintenance and repair information

For detailed information and usage instructions, please [click here to jump](https://docs.elephantrobotics.com/docs/gitbook-en/4-BasicApplication/4.1-myStudio/)

![1.1](../../../resourse/20-myAgv2023/myStudio/1.1.png)

###### myBlockly

It is a puzzle programming software based on the Python environment and related pymybot libraries. It allows users to program in a block-based manner to control myCobot. It is suitable for programming learners and can help train their programming logic skills. myBlockly also provides a Python display interface, which can translate user-built myBlockly programs into Python language to assist users in learning Python statements.

If you want to view the software's usage and examples, [click here to jump](https://docs.elephantrobotics.com/docs/gitbook-en/5-ProgramingApplication-myblockly-uiflow-mind/5.1-myBlockly/5.1.1The_First-Time_Use.html##running-program).

![1.1](../../../resourse/20-myAgv2023/myBlockly/1.1.png)

######  myAGV 2023 Visualization Software

It is software developed based on Python, designed for convenient use of the various functions of myAGV 2023. It also supports basic functionality testing of myAGV 2023 to help users quickly get started with myAGV 2023.

If you want to view the software's usage and examples, [click here to jump](https://docs.elephantrobotics.com/docs/gitbook-en/5-ProgramingApplication-myblockly-uiflow-mind/5.1-myBlockly/5.1.1The_First-Time_Use.html##running-program).

![Softeware Page](../../../resourse/20-myAgv2023/AGV_UI/software_page_cn.png "Software Page")

##### Network Connection

**Wired Connection**

Upon opening myAGV 2023, it is, by default, connected to the hotspot configured in the system: **ElephantRobotics_AP_XXXX**.

![Ubuntu2](../../../resourse/20-myAgv2023/PI/Ubuntu2.png)

Click on **"Disconnect"** to disconnect from the default hotspot.

![img](../../../resourse/20-myAgv2023/PI/Ubuntu3.png)

Connect the Ethernet cable to the network port on the robotic arm.

![网口](../../../resourse/20-myAgv2023/PI/Ethernet.jpg)

Connect a standard internet Ethernet cable to the network port on the robotic arm.

![img](../../../resourse/20-myAgv2023/PI/Ubuntu4.png)

**Wireless Connection**

There are two methods for wireless connection, and the first method requires an external display to perform some system operations. The specific steps are as follows:

First, click on **"Disconnect"** to close the default hotspot.

![Ubuntu5](../../../resourse/20-myAgv2023/PI/Ubuntu5.png)

Click on **"Enable Wi-Fi"**, and wait for the currently available Wi-Fi networks to be displayed.

![Ubuntu6](../../../resourse/20-myAgv2023/PI/Ubuntu6.png)

Click on the Wi-Fi network you want to connect to, and enter the Wi-Fi password.

![Ubuntu7](../../../resourse/20-myAgv2023/PI/Ubuntu7.png)

After successfully connecting, click on **"Connection Information"** to check the current IP address of the robotic arm.

![Ubuntu8](../../../resourse/20-myAgv2023/PI/Ubuntu8.png)

As shown in the example, **"192.168.10.64"** is the current IP address of the robotic arm.

![Ubuntu9](../../../resourse/20-myAgv2023/PI/Ubuntu9.png)

Connect your computer and the robotic arm to the same Wi-Fi network, open VNC viewer software, enter this IP address (in the example provided above, it would be **192.168.10.64**), and press Enter. The password is "Elephant," and the username is usually left blank. A successful connection will be similar to the example shown below.

![Ubuntu10](../../../resourse/20-myAgv2023/PI/Ubuntu10.png)

**The second method does not require a display screen; you can directly use your PC to connect to the Ubuntu system's hotspot for remote control. However, this connection method does not provide internet browsing capabilities; it is solely for remote control of the robotic arm system. The specific steps are as follows:**

Select the Ubuntu system hotspot **ElephantRobotics_AP_XXXX** on your PC and enter the password **Elephant**.

![Ubuntu11](../../../resourse/20-myAgv2023/PI/Ubuntu11.png)

Open VNC viewer software, enter the IP address **10.42.0.1**, and press Enter. The password is "Elephant," and the username is usually left blank. A successful connection will be similar to the example shown below.

![img](../../../resourse/20-myAgv2023/PI/Ubuntu12.png)

### 1.2 Introduction to the Development Environments Included in the System

#### Ros

[Development based on ROS](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/). ROS is an open-source operating system or auxiliary operating system used for robot control. With ROS, you can simulate and control myAGV 2023 in a virtual environment. myAGV 2023 can be visualized through the rviz platform and operated in various ways. After [installing the ROS development environment](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.2-环境搭建.html), please refer to the [usage cases](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.4-rivz介绍及使用/) and [how to use Moveit](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.5-Moveit/) for more information.

![导航修改起始点](../../../resourse/20-myAgv2023/PI/navigation_modify_startpoint.png)

#### Python

![2.1.5.4-1-006](../../../resourse/20-myAgv2023/PI/2.1.5.4-1-006.png)

[Development based on Python](https://docs.elephantrobotics.com/docs/gitbook-en/7-ApplicationBasePython/). Our robots support Python, and the development of Python API libraries is becoming more comprehensive, supporting control in various directions for myAGV 2023. For more information, please visit [Installing Python Environment](https://docs.elephantrobotics.com/docs/gitbook-en/7-ApplicationBasePython/7.1_download.html).

### 1.3 How to Reset the System

When the system is damaged due to improper operation or misconfiguration that cannot be corrected, you can reflash the system image to restore it to its initial settings (you will need an SD card reader).

For detailed steps, you can [click here to jump](https://docs.elephantrobotics.com/docs/gitbook-en/19-mirroring/镜像与烧录/15.2-burning.html).

![镜像烧录](../../../resourse/20-myAgv2023/PI/mirroring-burning.png)



## [2 Gamepad Control](https://docs.elephantrobotics.com/docs/gitbook/13-AdvancedKit/13.2移动机器人/13.2.5-ps2手柄控制.html)

You can control the movement of the machine using a gamepad and use the gripper or suction pump to grasp objects.

![handle](https://docs.elephantrobotics.com/docs/gitbook/resourse/2-serialproduct/2.1-280/M5/2.1.1.4%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E4%B8%8E%E6%90%AD%E5%BB%BA/2.3.jpg)

## [3 Python-Based Development and Usage](https://docs.elephantrobotics.com/docs/gitbook/7-ApplicationBasePython/)

Our robots support Python, and the development of Python API libraries is becoming more comprehensive. You can control various aspects of the robot, such as joint angles, coordinates, grippers, using Python. For more information, please refer to [Installing the Python Environment](https://docs.elephantrobotics.com/docs/gitbook/7-ApplicationBasePython/7.1_download.html).

![2.1.5.4-1-006](../../../resourse/20-myAgv2023/PI/2.1.5.4-1-006.png)

## [4 Blockly-Based Development and Usage](https://docs.elephantrobotics.com/docs/gitbook/5-ProgramingApplication-myblockly-uiflow-mind/)

myBlockly is a fully visual modular programming software and belongs to the graphical programming language category.

![1.1](../../../resourse/20-myAgv2023/myBlockly/1.1.png)

## [5 Development with ROS](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/)

ROS is an open-source, secondary operating system used for robot control. Through ROS, we can achieve simulation control of the robotic arm in a virtual environment. We visualize the robotic arm using the rviz platform and operate our robotic arm in various ways. We plan and execute the robotic arm's motion paths through the moveit platform to achieve free control of the robotic arm. After [installing the ROS development environment](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.2-环境搭建.html), you can refer to [usage cases](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.4-rivz介绍及使用/) and [how to use Moveit](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.1-ROS1/12.1.5-Moveit/) for more details.

The advent of ROS solved the communication problem of various robot components. Over time, more and more robot algorithms have been integrated into ROS. **ROS2** inherits from **ROS** and is more powerful and better. Compared to **ROS**, which only supports Linux systems, **ROS2** also supports **Windows**, **macOS**, and even **RTOS** platforms. After [installing the ROS2 development environment](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.2-ROS2/12.2.1-ROS2的安装.html), you can check [ROS2 usage cases](https://docs.elephantrobotics.com/docs/gitbook/12-ApplicationBaseROS/12.2-ROS2/12.2.4-rviz介绍及使用/) for more details.

![导航修改起始点](../../../resourse/20-myAgv2023/PI/navigation_modify_startpoint.png)

# Advanced Development

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/20-myAgv2023/video/agv2023_advanced_develope_en.mp4"></video>