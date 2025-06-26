# rviz的简单介绍及使用

rviz是ROS中一款三维可视化平台，一方面能够实现对外部信息的图形化显示，另外还可以通过 rviz 给对象发布控制信息，从而实现对机器人的监测与控制。

## rviz的安装及界面简介

在安装ros时，如果执行的完全安装，rviz已经安装好了,您可以直接尝试运行；如果没有完全安装，可单独安装rviz:

```bash
# Ubuntu16.04
sudo apt-get install ros-kinetic-rviz  
```
``` bash
# Ubuntu18.04
sudo apt-get install ros-melodic-rviz   
```
```bash
# Ubuntu20.04
sudo apt-get install ros-noetic-rviz    
```

安装完成后，请先打开一个新的终端(快捷键<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>),输入如下指令：
```bash
roscore
```

然后再打开一个一个新的终端(快捷键<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>)输入命令打开rviz

```bash
rosrun rviz rviz
# 或
rviz
```

打开rviz,显示如下界面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz-1.png
width ="500"  align = "center">

### 各个区域介绍

+ 左侧为显示器列表，显示器是在3D世界中绘制某些内容的东西，并且可能在显示列表中具有一些可用的选项。
+ 上方是工具栏，允许用户用各种功能按键选择多种功能的工具
+ 中间部分为3D视图: 它是可以用三维方式查看各种数据的主屏幕。3D视图的背景颜色、固定框架、网格等可以在左侧显示的全局选项（Global Options）和网格（Grid）项目中进行详细设置。
+ 下方为时间显示区域，包括系统时间和ROS时间等。
+ 右侧为观测视角设置区域，可以设置不同的观测视角。

本部分我们只进行粗略的介绍，如果您想了解更多详细的内容，可以前往[用户指南](http://wiki.ros.org/rviz/UserGuide)进行查看。

## mycobot_ros安装与更新

- **M5版本：** 请查看 ROS1环境搭建 章节末尾。

## 简单使用

**通过launch文件启动**

本例子建立在您已经完成[环境搭建](../12.1.2-环境搭建.md)，并成功将本公司的代码从GitHub上复制下来的基础上。

打开一个控制台终端(快捷键<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>)
输入一下命令进行**ROS的环境配置**。

```bash
cd ~/catkin_ws/
source devel/setup.bash
```

再输入：

- mycobot 280-M5版本：

```bash
roslaunch mycobot_280 test.launch
```

打开rviz，并得到如下结果：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz-5.png
width ="500"  align = "center">

如果您想了解更多rviz的相关资料信息，您可以前往[官方文档](http://wiki.ros.org/rviz)进行查看


## M5版本前提条件

- 打开控制台终端（ 快捷键 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd> )，打开终端窗口查看设备名称：

```bash
# 查看机械臂的设备名称
ls /dev/ttyUSB* # 旧版本 myCobot280 M5   

# 如果终端没有显示/dev/ttyUSB相关名称，需要使用如下命令
ls /dev/ttyACM* # 新版本 myCobot280 M5
```

- 授予机械臂串口权限：

```bash
# 默认设备名是/dev/ttyUSB0，如果设备名不是默认值，需要修改。
sudo chmod 777 /dev/ttyUSB0 # 旧版本 myCobot280 M5 

sudo chmod 777 /dev/ttyACM0 # 新版本 myCobot280 M5
```

然后输入用户密码（**注意：** 输入密码是不显示的，输入正确即可）。



# 280系列rviz使用指南

## 机械臂的控制

>>**注意：** 为了更好的运动效果，端臂的Atom固件版本为6.5，python驱动库pymycobot版本为3.5.3

### 滑块控制

打开一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 slider_control.launch port:=/dev/ttyUSB0 baud:=115200
```
它将**打开 rviz 和一个滑块组件**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/caf-1.png
width ="500"  align = "center">

接着你可以**通过拖动滑块来控制 rviz 中的模型移动**。如果你想让真实的 mycobot 跟着一起运动，需要再打开一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**请注意：由于在命令输入的同时机械臂会移动到模型目前的位置，在您使用命令之前请确保rviz中的模型没有出现穿模现象**
**不要在连接机械臂后做出快速拖动滑块的行为，防止机械臂损坏**

### 模型跟随

除了上面的控制，我们也可以**让模型跟随真实的机械臂运动**。打开一个命令行运行：
- mycobot 280-M5版本：
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 follow_display.py _port:=/dev/ttyUSB0 _baud:=115200
```


然后打开另一个命令行，运行：
- mycobot 280-M5版本：
```bash
roslaunch mycobot_280 mycobot_follow.launch
```
它将**打开 rviz 展示模型跟随效果**。

### GUI 控制

在前面的基础上，本包还**提供了简单的 Gui 控制界面**。 该方式意在于真实机械臂相互联动，请连接 mycobot。

打开命令行：
- mycobot 280-M5版本：
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 simple_gui.launch port:=/dev/ttyUSB0 baud:=115200
```
<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/gui-1.png
width ="500"  align = "center">

### 键盘控制

在 `mycobot_280` 的包中**添加了键盘控制的功能**，并在 rviz 中实时同步。本功能依赖 pythonApi，所以确保与真实机械臂连接。

打开一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard.launch port:=/dev/ttyUSB0 baud:=115200
```

运行效果如下：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/kb-1.png
width ="500"  align = "center">

命令行中将会输出 mycobot 信息，如下：
```bash
SUMMARY
========

PARAMETERS
 * /mycobot_services/baud: 115200
 * /mycobot_services/port: /dev/ttyUSB0
 * /robot_description: <?xml version="1....
 * /rosdistro: kinetic
 * /rosversion: 1.12.1.17

NODES
  /
    mycobot_services (mycobot_280/mycobot_services.py)
    real_listener (mycobot_280/listen_real.py)
    robot_state_publisher (robot_state_publisher/state_publisher)
    rviz (rviz/rviz)

auto-starting new master
process[master]: started with pid [1333]
ROS_MASTER_URI=http://localhost:11311

setting /run_id to f977b3f4-b3a9-11eb-b0c8-d0c63728b379
process[rosout-1]: started with pid [1349]
started core service [/rosout]
process[robot_state_publisher-2]: started with pid [1357]
process[rviz-3]: started with pid [1367]
process[mycobot_services-4]: started with pid [1380]
process[real_listener-5]: started with pid [1395]
[INFO] [1620882819.196217]: start ...
[INFO] [1620882819.205050]: /dev/ttyUSB0,115200

MyCobot Status
--------------------------------
Joint Limit:
    joint 1: -170 ~ +170
    joint 2: -170 ~ +170
    joint 3: -170 ~ +170
    joint 4: -170 ~ +170
    joint 5: -170 ~ +170
    joint 6: -180 ~ +180

Connect Status: True

Servo Infomation: all connected

Servo Temperature: unknown

Atom Version: unknown

[INFO] [1620882819.435778]: ready
```


接着，打开另一个命令行，运行：


- mycobot 280-M5版本：

```bash
rosrun mycobot_280 teleop_keyboard.py
#或者
rosrun mycobot_280 teleop_keyboard.py _speed:=70
```


你会在命令行中看到如下输出：
```bash
Mycobot Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx,ry,rz]):
              w(x+)

    a(y-)     s(x-)     d(y+)

    z(z-) x(z+)

u(rx+)   i(ry+)   o(rz+)
j(rx-)   k(ry-)   l(rz-)

Gripper control:
    g - open
    h - close

Other:
    1 - Go to init pose
    2 - Go to home pose
    3 - Resave home pose
    q - Quit

currently:      speed: 50       change percent 5
```

在该终端中，您可以通过命令行中的按键控制机械臂的状态和对机械臂进行移动操作。

该脚本支持的参数：

+ _speed：机械臂移动速度。

+ _change_percent：移动距离百分比。

### 视觉

>将相机安装在 mycobot 的末端。 本视觉部分使用 eye-in-hand 的方式。重新安装相机之后，需进行一次手眼标定。

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/camera_connect-1.jpg
width ="500"  align = "center">

#### 使用前提

##### python依赖库

使用pip安装以下python库

```bash
pip install stag-python

pip install opencv-python

pip install scipy

pip install numpy

pip install pymycobot
```

##### Stag码

本文使用stag码用作二维码跟踪，建议使用彩印，黑白打印识别率较低。

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/stag.png
width ="500"  align = "center">

下载地址: [Stag码下载](https://drive.google.com/drive/folders/0ByNTNYCAhWbILXd2SE5FY1c3WXM?resourcekey=0-nWeENtNZql2j9AF32Ud8sQ)

**注意**：stag码的左上角为编号，使用opencv的stag识别库可以识别该编号，你可以为不同编号设计不同的行为逻辑，比如00设为位置跟踪，01设为姿态跟踪，02设为回到观测点。

##### 固件更新

使用stag跟踪专用固件效果更佳，该固件会限制机械臂的姿态偏转，在刷新模式下使用send_coords接口会筛选掉角度偏差超过90°的相邻坐标。

固件名为 `mycobot280_atom0926_vision.bin`, 位于本项目的 `~/mycobot_ros/mycobot_280/mycobot_280/config`文件夹下

##### 相机初始化

在本项目的`~/mycobot_ros/mycobot_280/mycobot_280/camera_calibration/camera_calibration.py`文件中定义了名为camera_detect的视觉识别类

```bash
class camera_detect:
    #Camera parameter initialize
    def __init__(self, camera_id, marker_size, mtx, dist):
```

其初始化的四个参数分别为：

```bash
camera_id 相机编号（范围一般是0~10，默认为0）
marker_size Stag码的边长（mm）
mtx, dist 相机参数
```

在程序中已经给了初始化的示例，用户仅需修改camera_id和marker_size即可

```bash
camera_params = np.load("camera_params.npz")  # 相机配置文件
mtx, dist = camera_params["mtx"], camera_params["dist"]
m = camera_detect(0, 32, mtx, dist)
```

**注意**: Linux系统下的camera_id一般默认是 0，如果错误，则修改成其他 0 ~ 10的参数。

#### 手眼标定

##### 手眼矩阵原理

手眼标定是视觉跟踪必不可少的一环，其作用是求得机械臂坐标系（手）与相机坐标系（眼）之间的相对关系，我们把这种相对关系用一个4*4的手眼矩阵来表示，具体原理可以参考：[手眼矩阵原理](https://blog.csdn.net/weixin_45844515/article/details/125571550)

##### 手眼标定方法

> **注意：** 重新安装相机之后，需进行一次手眼标定。

将相机装配到机械臂上（一般装配在机械臂末端），连接需要控制的机械臂

命令行运行：

- mycobot 280-M5版本：
  
```python
cd ~/mycobot_ros/mycobot_280/mycobot_280/camera_calibration  # 终端切换到目标路径
python3 camera_calibration.py  # 相机id， 默认为 0.
```

此时机械臂会先运动到观测姿态

```python
self.origin_mycbot_level = [0, 5, -104, 14, 0, 0]
def Eyes_in_hand_calibration(self, ml):
    ml.send_angles(self.origin_mycbot_level, 50)  # 移动到观测点
```

**注意**： 用户可自定义修改观测点位，比如旋转6关节使相机处于更合适的位置。

1. 运动到观测姿态后，终端会弹出以下提示，将stag码置于相机视野内，输入任意键即可继续识别

```bash
make sure camera can observe the stag, enter any key quit
```

2.若相机识别到stag码，则会自动进入下一步识别，机械臂移动并捕捉机械臂和相机的位置信息

```bash
Move the end of the robot arm to the calibration point, press any key to release servo
```

3. 贴紧后根据提示，输入任意键完成手眼标定

```bash
focus servo and get current coords
```

4. 此时会打印EyesInHand_matrix信息，视为标定完成，生成"EyesInHand_matrix.json配置文件，标定成功后无需重复操作！

具体效果参考如下视频，效果与mycobot 280类似：

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/mycobot_hand_vision.mp4" type='video/mp4' >
</video>

**注意**：**手眼标定可能会由于操作不当、机器虚位等原因出现误差，当视觉跟踪效果不好时，需要重新手眼标定**

#### 视觉跟踪

>> 本案例机械臂的控制方式：使用ROS中的话题进行通信。
USB相机启动方式：使用ROS中的相机usb_cam节点进行启动。

usb_cam 安装命令：

```bash
# Ubuntu 20.04 
sudo apt install ros-noetic-usb-cam   
```

主要涉及代码文件：

[1. communication_topic.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_communication/launch/communication_topic.launch)

[2. mycobot_topics.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_communication/scripts/mycobot_topics.py)

[3. open_camera.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/launch/open_camera.launch)

[4. listen_real_of_topic.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/scripts/listen_real_of_topic.py)

[5. detect_marker_with_topic.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/launch/detect_marker_with_topic.launch)

[6. detect_stag.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/scripts/detect_stag.py)

其中相机文件 `open_camera.launch` 中的相机设备参数默认为 `/dev/video0`.

```bash
<!-- //指定设备文件名，默认是/dev/video0 -->
    <param name="video_device" value="/dev/video0" />
```

命令行运行：

- mycobot 280-M5版本：
  
```bash
cd ~/catkin_ws
source devel/setup.bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 detect_marker_with_topic.launch port:=/dev/ttyUSB0 baud:=115200
```

+ port： 串口字符串
+ baud： 波特率

将实时显示 mycobot 的状态。

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/vision-5.png
width ="500"  align = "center">

紧接着运行stag识别跟踪脚本。打开新的命令行：

- mycobot 280-M5版本：

```bash
cd ~/catkin_ws
source devel/setup.bash
rosrun mycobot_280 detect_stag.py
```

启动后，机械臂会运动到观测点

```bash
self.origin_mycbot_horizontal = [0,60,-60,0,0,0]
ml.send_angles(self.origin_mycbot_horizontal, 50)  # 移动到观测点
```

具体效果如下：

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/280_vision.mp4" type='video/mp4' >
</video>

### 末端执行器

- **支持的末端执行器：** myCobot自适应夹爪、myCobot垂直吸泵V2.0、摄像头法兰
- **适用设备：** myCobot 280 M5、myCobot 280 PI

> 注意：myCobot自适应夹爪仅支持 myCobot 280 M5 设备

#### myCobot自适应夹爪

##### 加载模型

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
roslaunch mycobot_280 test_gripper.launch
```

它将**打开rviz**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-10.png
width ="500"  align = "center">

#####  滑块控制

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 slider_control_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

它将**打开rviz和一个滑块组件**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-11.png
width ="500"  align = "center">

接着你可以**通过拖动滑块来控制 rviz 中的模型移动。** 如果你想让真实的 myCobot 跟着一起运动，需要**再打开一个命令行**，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 slider_control_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```

**请注意：由于在命令输入的同时机械臂会移动到模型目前的位置，在您使用命令之前请确保rviz中的模型没有出现穿模现象**。
**不要在连接机械臂后做出快速拖动滑块的行为，防止机械臂损坏**。

##### 模型跟随

除了上面的控制，我们也可以**让模型跟随真实的机械臂运动**。打开一个命令行运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 follow_display_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```

然后打开另一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
roslaunch mycobot_280 mycobot_follow_gripper.launch
```

它将**打开 rviz 展示模型跟随效果**。

##### GUI控制

在前面的基础上，本包还**提供了简单的 Gui 控制界面**。 该方式意在于真实机械臂相互联动，请连接 myCobot。

打开命令行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 simple_gui_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

它将**打开rviz和一个GUI界面**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-12.png
width ="500"  align = "center">

#####  键盘控制

在 `mycobot_280` 的包中**添加了键盘控制的功能**，并在 rviz 中实时同步。本功能依赖 pythonApi，所以确保与真实机械臂连接。

打开一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

运行效果如下：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-10.png
width ="500"  align = "center">

命令行中将会输出 mycobot 信息，如下：

```bash
SUMMARY
========

PARAMETERS
 * /mycobot_services/baud: 115200
 * /mycobot_services/port: /dev/ttyUSB0
 * /robot_description: <?xml version="1....
 * /rosdistro: kinetic
 * /rosversion: 1.12.1.17

NODES
  /
    mycobot_services (mycobot_280/mycobot_services.py)
    real_listener (mycobot_280/listen_real.py)
    robot_state_publisher (robot_state_publisher/state_publisher)
    rviz (rviz/rviz)

auto-starting new master
process[master]: started with pid [1333]
ROS_MASTER_URI=http://localhost:11311

setting /run_id to f977b3f4-b3a9-11eb-b0c8-d0c63728b379
process[rosout-1]: started with pid [1349]
started core service [/rosout]
process[robot_state_publisher-2]: started with pid [1357]
process[rviz-3]: started with pid [1367]
process[mycobot_services-4]: started with pid [1380]
process[real_listener-5]: started with pid [1395]
[INFO] [1620882819.196217]: start ...
[INFO] [1620882819.205050]: /dev/ttyUSB0,115200

MyCobot Status
--------------------------------
Joint Limit:
    joint 1: -170 ~ +170
    joint 2: -135 ~ +140
    joint 3: -150 ~ +150
    joint 4: -145 ~ +135
    joint 5: -170 ~ +170
    joint 6: -180 ~ +180

Connect Status: True

Servo Infomation: all connected

Servo Temperature: unknown

Atom Version: unknown

[INFO] [1620882819.435778]: ready
```

接着，打开另一个命令行，运行：

- mycobot 280-M5版本：

```bash
rosrun mycobot_280 teleop_keyboard.py
```

你会在命令行中看到如下输出：

```bash
Mycobot Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx,ry,rz]):
              w(x+)

    a(y-)     s(x-)     d(y+)

    z(z-) x(z+)

u(rx+)   i(ry+)   o(rz+)
j(rx-)   k(ry-)   l(rz-)

Gripper control:
    g - open
    h - close

Pump control:
    b - open
    m - close
    
Other:
    1 - Go to init pose
    2 - Go to home pose
    3 - Resave home pose
    q - Quit

currently:      speed: 50       change percent 5
```

在该终端中，您可以通过命令行中的按键控制机械臂的状态和对机械臂进行移动操作。

该脚本支持的参数：

+ _speed：机械臂移动速度。
+ _change_percent：移动距离百分比。

#### 6.2 myCobot垂直吸泵V2.0

##### 1 加载模型

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
roslaunch mycobot_280 test_pump.launch
```

它将**打开rviz**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-13.png
width ="500"  align = "center">

##### 2 滑块控制

> **注意：该功能仅支持对机械臂的控制**

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 slider_control_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

它将**打开rviz和一个滑块组件**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-16.png
width ="500"  align = "center">

接着你可以**通过拖动滑块来控制 rviz 中的模型移动。** 如果你想让真实的 myCobot 跟着一起运动，需要**再打开一个命令行**，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**请注意：由于在命令输入的同时机械臂会移动到模型目前的位置，在您使用命令之前请确保rviz中的模型没有出现穿模现象**。
**不要在连接机械臂后做出快速拖动滑块的行为，防止机械臂损坏**。

##### GUI控制

在前面的基础上，本包还**提供了简单的 Gui 控制界面**。 该方式意在于真实机械臂相互联动，请连接 myCobot。

打开命令行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 simple_gui_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

它将**打开rviz和一个GUI界面**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-14.png
width ="500"  align = "center">

##### 键盘控制

在 `mycobot_280` 的包中**添加了键盘控制的功能**，并在 rviz 中实时同步。本功能依赖 python API，所以确保与真实机械臂连接。

打开一个命令行，运行：

- mycobot 280-M5版本：
  
```bash
# mycobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

运行效果如下：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-13.png
width ="500"  align = "center">

接着，打开另一个命令行，运行：

- mycobot 280-M5版本：

```bash
rosrun mycobot_280 teleop_keyboard.py
```

你会在命令行中看到如下输出：

```bash
Mycobot Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx,ry,rz]):
              w(x+)

    a(y-)     s(x-)     d(y+)

    z(z-) x(z+)

u(rx+)   i(ry+)   o(rz+)
j(rx-)   k(ry-)   l(rz-)

Gripper control:
    g - open
    h - close

Pump control:
    b - open
    m - close
    
Other:
    1 - Go to init pose
    2 - Go to home pose
    3 - Resave home pose
    q - Quit

currently:      speed: 50       change percent 5
```

在该终端中，您可以通过命令行中的按键控制机械臂的状态和对机械臂进行移动操作。

该脚本支持的参数：

+ _speed：机械臂移动速度。
+ _change_percent：移动距离百分比。

#### 摄像头法兰

##### 1 加载模型

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
roslaunch mycobot_280 test_camera_flange.launch
```

它将**打开rviz**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-15.png
width ="500"  align = "center">

##### 2 滑块控制

> **注意：该功能仅支持对机械臂的控制**

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
roslaunch mycobot_280 slider_control_camera_flange.launch port:=/dev/ttyUSB0 baud:=115200
```

它将**打开rviz和一个滑块组件**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-17.png
width ="500"  align = "center">

接着你可以**通过拖动滑块来控制 rviz 中的模型移动。** 如果你想让真实的 myCobot 跟着一起运动，需要**再打开一个命令行**，运行：

- myCobot 280-M5版本：

```bash
# myCobot 280-M5版本默认串口名为"/dev/ttyUSB0"，波特率为115200.部分机型的串口名为 "dev/ttyACM0",若默认串口名发生错误，可将串口名改为"/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**请注意：由于在命令输入的同时机械臂会移动到模型目前的位置，在您使用命令之前请确保rviz中的模型没有出现穿模现象**。
**不要在连接机械臂后做出快速拖动滑块的行为，防止机械臂损坏**。

####  摄像头法兰 && 吸泵

##### 1 加载模型

打开一个命令行，运行：

- myCobot 280-M5版本：

```bash
roslaunch mycobot_280 test_camera_flange_pump.launch
```

它将**打开rviz**，你将看到如下画面：

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-18.png
width ="500"  align = "center">

#### URDF模型地址

##### 1 myCobot 自适应夹爪

- [myCobot 280-M5 版本](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_gripper_parallel.urdf)

##### 2 myCobot 垂直吸泵V2.0

- [myCobot 280-M5 版本](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_pump.urdf)
##### 3 摄像头法兰

- [myCobot 280-M5 版本](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange.urdf)

##### 4 摄像头法兰 && 吸泵

- [myCobot 280-M5 版本](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange_pump.urdf)