## ROS Introduction

**ROS** is the abbreviation of robot operating system. **ROS** is a highly flexible software architecture for writing robot software programs.


 <img src =../../../resourse/12-ApplicationBaseROS/icon.png
 align = "center">


**ROS** is of open source and is a post-operating system or secondary operating system for controlling robots. It provides the functions similar to those provided by an operating system, including hardware abstraction description, low-level driver management, execution of common functions, messages transferred between programs, and program release package management. It also provide some tool programs and libraries used to get, create, write and run multi-machine integration programs.

The primary design goal of **ROS** is to improve the code reuse rate in the R&D field of robots. **ROS** is a framework (i.e. "nodes") for distributed processes, which are encapsulated in program and function packages that can be easily shared and distributed. **ROS** also supports a federated system similar to a code repository, and this system also enables the collaboration and distribution of a project. This design enables the development and realization of a project to to be decided completely independently from the file system to the user interface (no limit by **ROS**). At the same time, all projects can be integrated with the basic tools of **ROS**.

**Notice**:

- Burn the corresponding firmware by using  [**mystudio**](../../../4-BasicApplication/4.1-myStudio/README.md). Among them, burn minirobot in M5Stack-basic, select the transponder function, and burn the latest version of atommain in atom.
-  With Ubuntu 20.04 system, **myBuddy** has built-in development environment, which can be used directly.
- If you use ROS to connect to **myBuddy** through a remote **Python Socket**, you need to build a ROS-related environment **on the remote PC**. For details, please refer to [12.1.2 Environment Building](12-ApplicationBaseROS/12.1-ROS1/12.1.2-环境搭建.md)
- ROS1 version support: Ubuntu 20.04 / ROS1 Noetic
- ROS2 version support: Ubuntu 20.04 / ROS2 Foxy / ROS2 Galactic (**myBuddy** already has a ROS2 Galactic version built in)

---

## Application of ROS in myBuddy
In order to drive  **myBuddy** through ROS, two tools, rviz and moveit, will be introduced next.
- Rviz is a three-dimensional visualization platform in ROS, which can realize the graphical display of external information. In addition, it can release control information to the manipulator through rviz, so as to realize the monitoring and control of the robot. The [**Rviz**](rviz介绍及使用.md) section will introduce two control methods of **myBuddy**: Slider Control and Mobile Follow.
- **Moveit** is an integrated development platform in ROS, which is composed of a variety of function packages for manipulating manipulator, including motion planning, operation, control, inverse kinematics, 3D perception and collision detection. The [**Moveit**](moveit.md) section will introduce four kinds of control groups of **myBuddy**: the control group is used to realize the partial and overall control of the left arm, right arm and waist.

## mycobot_ros installation and update

`mycobot_ros` is a ROS package from ElephantRobotics that works with all types of desktop robots.

The address of the project: [https://github.com/elephantrobotics/mycobot_ros](https://github.com/elephantrobotics/mycobot_ros)

`<ros-workspace>` is used to stand for the workspace path of ROS in the computer in the following part.The official default is `catkin_ws`. Be sure to replace `<ros-workspace>` with the real path of your local machine when executing the following command.

Click the `ROS1 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-1.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-2.jpg
 align = "center">

Then enter the following command:

```bash
cd ~/<ros-workspace>/src  # Enter the src folder of the workspace
# Clone the code on github
git clone https://github.com/elephantrobotics/mycobot_ros.git
cd ..       # return to the workspace
catkin_make # Build the code in the workspace
source devel/setup.bash # add environment variables
```

**Note:** If the `/home/ubuntu/catkin_ws/src(equivalent to ~/catkin_ws/src)` already exists in the `mycobot_ros` folder, you need to delete the `mycobot_ros` folder before running the above command. In the directory path, `ubuntu` is the user name of the VM. If they are different, change them.

## mycobot_ros2 installation and update

`mycobot_ros2` is a ROS package from ElephantRobotics that works with all types of desktop robots.

The address of the project: [https://github.com/elephantrobotics/mycobot_ros2](https://github.com/elephantrobotics/mycobot_ros2)

`<ros2-workspace>` is used to stand for the workspace path of ROS in the computer in the following part.The official default is `colcon_ws`. Be sure to replace `<ros2-workspace>` with the real path of your local machine when executing the following command.

Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/17-myBuddy/ROS/17.4.3-17.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-18.jpg
 align = "center">
    <img src =../../../resourse/17-myBuddy/ROS/17.4.3-19.jpg
 align = "center">

Then enter the following command:

```bash
cd ~/<ros2-workspace>/src  # Enter the src folder of the workspace
# Clone the code on github
git clone https://github.com/elephantrobotics/mycobot_ros2.git
cd ..       # return to the workspace
colcon build --symlink-install # Build the code in the workspace, --symlink-install: Avoid having to recompile python scripts every time you adjust them
source install/setup.bash # add environment variables
```

**Note:** If the `/home/er/colcon/src(equivalent to ~/colcon_ws/src)` already exists in the `mycobot_ros2` folder, you need to delete the `mycobot_ros2` folder before running the above command.
