# ROS/ROS2 Introduction

**ROS** is the abbreviation of robot operating system. **ROS** is a highly flexible software architecture for writing robot software programs.

**Notice**:
- Currently, **myCobot 280 series**、**myCobot 320 series** 、**myPalletizer 260 series**、**mechArm 270 series** support the use of ROS. for specific situation of the development of various equipment, refer to [**equipment development**](../4-BasicApplication/README.md).
- Burn the corresponding firmware by using [**mystudio**](../4-BasicApplication/4.1-myStudio/README.md). Burn the minirobot in M5Stack-basic, choose the transponder function, and burn the latest version of atomMain in atom.

**ROS Logo** ：

![ROS Logo](../resourse/12-ApplicationBaseROS/icon.png)

**ROS** is of open source and is a post-operating system or secondary operating system for controlling robots. It provides the functions similar to those provided by an operating system, including hardware abstraction description, low-level driver management, execution of common functions, messages transferred between programs, and program release package management. It also provide some tool programs and libraries used to get, create, write and run multi-machine integration programs.

The primary design goal of **ROS** is to improve the code reuse rate in the R&D field of robots. **ROS** is a framework (i.e. "nodes") for distributed processes, which are encapsulated in program and function packages that can be easily shared and distributed. **ROS** also supports a federated system similar to a code repository, and this system also enables the collaboration and distribution of a project. This design enables the development and realization of a project to to be decided completely independently from the file system to the user interface (no limit by **ROS**). At the same time, all projects can be integrated with the basic tools of **ROS**.

Due to the following disadvantages of **ROS**:

- Limited real-time communication
- System stability does not yet meet industrial-grade requirements
- No security measures
- Only supports Linux(ubuntu)
- The performance of the core mechanism is not optimized to occupy resources

Therefore, **ROS** cannot really enter the industry, and naturally cannot be commercialized. To solve this problem, the community proposed **ROS 2**. It makes **ROS** have the characteristics of productization, including real-time performance, adaptability to all platforms, suitable for hardware with low performance (MCU+RTOS), distributed, data encryption and support for modern programming languages.

**ROS2** first removes the master node that exists in **ROS**. After removing the master node, each node can discover each other through the DDS node, each node is equal, and can realize one-to-one, one-to-many, and many-to-many communication. After using DDS for communication, reliability and stability have been enhanced.

Compared with **ROS** that only supports Linux systems, **ROS2** also supports windows, mac, and even RTOS platforms.

**Applicable equipment:**

- myCobot 280
  - myCobot 280 M5
  - myCobot 280 PI
  - myCobot 280 Jetson Nano
  - myCobot 280 for Arduino <br>
- myCobot 320
  - myCobot 320 M5
  - myCobot 320 PI <br>
- myPalletizer 260
  - myPalletizer 260 M5
  - myPalletizer 260 PI <br>
- myCobot PRO 600 <br>
- mechArm-270
  - mechArm-270 M5
  - mechArm-270 PI

**Preconditions for use:**

- **M5** series version， the bottom **M5Stack-basic** is programmed to miniRobot , select the  **Transponder** function, and the end **ATOM** is programmed to the latest version of atomMain (the factory default has been programmed)
- **Pi \ jetsonnano** series, **ATOM** burns the latest version of **atomMain** (factory default already burnt)

**Device Description:**

+ Among the devices used above, mechArm-270 PI、myCobot 280-Pi, myCobot 280-JetsonNano, and myCobot 320-Pi versions have their own Ubantu (V-18.04 / V-20.04) system and have a built-in development environment, so they can be used directly without setting up management.

+ MyCobot 280-M5, myCobot 320-M5, myCobot 280-Arduino, myPalletizer 260, and mechArm-270-M5 versions need to be built in an environment, but in ROS/ROS2, you only need to [build a ROS environment](12.2-环境搭建.md) or [build a ROS2 environment](12.2-ROS2/12.2.1-ROS2的安装.md).



# MoveIt Introduction

**MoveIt** is currently the most advanced software for movement operations of robot arms and has been used for more than 100 robots. It integrates the latest achievements in motion planning, control, 3D perception, motion control, control and navigation, provides an easy-to-use platform for developing advanced robot applications, and provides an integrated software platform for design, and integration assessment of new robot products in the fields of industry, commerce, R&D, etc.

**MoveIt Logo** :

![MoveIt Logo](../resourse/12-ApplicationBaseROS/moveit-icon.png)

**Applicable equipment:**

- myCobot 280
  - myCobot 280 M5
  - myCobot 280 PI
  - myCobot 280 Jetson Nano
  - myCobot 280 for Arduino <br>
- myCobot 320
  - myCobot 320 M5
  - myCobot 320 PI <br>
- myPalletizer 260
  - myPalletizer 260 M5
  - myPalletizer 260 PI <br>
- myCobot PRO 600 <br>
- mechArm-270
  - mechArm-270 PI
  - mechArm-270 M5

**Preconditions for use:**

- **M5** series version， the bottom **M5Stack-basic** is programmed to miniRobot , select the  **Transponder** function, and the end **ATOM** is programmed to the latest version of atomMain (the factory default has been programmed)
- **Pi \ jetsonnano** series, **ATOM** burns the latest version of **atomMain** (factory default already burnt)
