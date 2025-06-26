# Introduction to ROS/ROS2

**ROS** is the abbreviation of Robot Operating System.
**ROS** is a highly flexible software architecture used to write robot software programs.

**Note**:

- At present, **myCobot 280 series**, **myCobot 320 series**, **myPalletizer260 series**, **mechArm270 series** all support the use of **ROS**. For the specific development of various devices, please refer to [**Device Development**](../4-BasicApplication/README.md).
- Use [**mystudio**](../4-BasicApplication/4.1-myStudio/README.md) to burn the corresponding firmware. Among them, burn minirobot in basic, select the transponder function, and burn the latest version of atomMain in atom.

**ROS Icon** :

![ROS Icon](../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROSicon.png)

**ROS** is open source and is a post-operating system, or secondary operating system, for robot control. It provides functions similar to those provided by an operating system, including hardware abstraction description, low-level driver management, execution of common functions, message passing between programs, and program distribution package management. It also provides some tool programs and libraries for obtaining, building, writing and running multi-machine integrated programs.

**ROS**'s primary design goal is to increase code reuse in the field of robotics research and development. **ROS** is a distributed process (that is, "node") framework that is encapsulated in program packages and function packages that are easy to share and publish. **ROS** also supports a federated system similar to a code repository, which can also realize project collaboration and release. This design allows the development of a project to achieve completely independent decisions from the file system to the user interface (not limited by **ROS**). At the same time, all projects can be integrated with the basic tools of **ROS**.

Due to the following shortcomings of ROS:

- Limited real-time communication
- System stability has not yet reached industrial-grade requirements
- No security measures
- Only supports Linux (ubuntu)
- Core mechanism performance is not optimized and occupies resources

Therefore, **ROS** cannot really enter the industry, and naturally cannot be commercialized. To solve this problem, the community proposed **ROS 2**. It makes **ROS** have product characteristics, including real-time, full-platform adaptability, suitable for low-performance hardware (MCU+RTOS), distributed, data encryption and support for modern programming languages.

**ROS2** first removes the master node existing in **ROS**. After removing the master node, each node can discover each other through the DDS node, and each node is equal, and one-to-one, one-to-many, and many-to-many communication can be achieved. After using DDS for communication, reliability and stability are enhanced.

Compared with **ROS** that only supports Linux systems, **ROS2** also supports windows, mac and even RTOS platforms.

**[ROS1 Development Guide](./12.1-ROS1/12.1.1-Introduction.md)**

**[ROS2 Development Guide](./12.2-ROS2/12.2.3-ROS2Introduction.md)**

**ROS Applicable Devices:**

- myCobot 280
- myCobot 280 M5
- myCobot 280 PI
- myCobot 280 Jetson Nano
- myCobot 280 for Arduino <br>

**Prerequisites:**

- **M5** series version, **M5Stack-basic** burn **miniRobot** at the bottom, select **Transponder** function, **ATOM** burn the latest version of **atomMain** at the end (factory default burned)

**Device description:**

- myCobot 280-M5, myCobot 320-M5, myCobot 280-Arduino, myPalletizer 260, mechArm-270-M5 and other versions need to build an environment for use, but in ROS/ROS2, you only need to build a ROS environment or a ROS2 environment.

# MoveIt Introduction

**MoveIt** is currently the most advanced software for robot arm mobile operations and has been used on more than 100 robots. It integrates the latest achievements in motion planning, control, 3D perception, control science, control and navigation, and provides an easy-to-use platform for developing advanced robot applications. It provides an integrated software platform for the design and integrated use evaluation of new robot products in the fields of industry, commerce and R&D.

**MoveIt Icon** :

![moveit Icon](../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/moveiticon.png)

**Applicable devices:**

- myCobot 280
- myCobot 280 M5
- myCobot 280 PI
- myCobot 280 Jetson Nano
- myCobot 280 for Arduino <br>

**Prerequisites:**

- **M5** series version, **M5Stack-basic** burn **miniRobot** at the bottom, select **Transponder** function, **ATOM** burn the latest version of **atomMain** at the end (factory default burned)