## MoveIt

### MoveIt 简介

MoveIt 是ROS中的一个集成开发平台，由多种用于操纵机械臂的功能包组成，包括：运动规划、操作、控制、逆运动学、3D感知和碰撞检测等。

下图所示为 Moveit 提供的主要节点 **move_group** 的高层结构，它像一个组合器：把所有单独的组件集成在一起，提供一系列的 actions 和 services 供用户使用。

<img src =../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS1/moveit/moveit-1.png
width ="500"  align = "center">

### 用户界面
用户可以通过三种方式访问move_group提供的操作和服务：

* 在C++ ： 使用move_group_interface包可以方便实用move_group。
* 在 Python ： 使用moveit_commander包。
* 通过 GUI ： 使用 Motion——commander 的 Rviz（ROS可视化工具）。

move_group可以使用ROS参数服务器进行配置，从中还可以获取机器人的URDF和SRDF。

###  配置
move_group是一个 ROS 节点。它使用ROS参数服务器来获取三种信息：

1. URDF - move_group在ROS参数服务器上查找robot_description参数，以获取机器人的URDF。

2. SRDF - move_group在 ROS 参数服务器上查找robot_description_semantic参数，以获取机器人的 SRDF。SRDF 通常由用户使用 MoveIt 设置助理创建。

3. MoveIt 配置 - move_group将在 ROS 参数服务器上查找特定于 MoveIt 的其他配置，包括关节限制、运动学、运动规划、感知和其他信息。这些组件的配置文件由MoveIt设置助手自动生成，并存储在机器人的相应MoveIt配置包的配置目录中。

## 如何使用MoveIt

>>**注意：** 为了更好的运动效果，端臂的Atom固件版本为6.5，python驱动库pymycobot版本为3.5.3

`mycobot_ros` 现已集成了 MoveIt 部分。

打开命令行运行：
- mycobot 280-M5版本：
  
```bash
roslaunch mycobot_280_moveit mycobot_moveit.launch
```


运行效果如下：  

<img src =../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS1/moveit/moveit-2.png
width ="500"  align = "center">

可以计划并执行，演示效果：

<img src =../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS1/moveit/moveit-3.gif
width ="500"  align = "center">

如果需要让真实的机械臂同步执行计划，需要再打开一个命令行，运行：
- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280_moveit sync_plan.py _port:=/dev/ttyUSB0 _baud:=115200
```
