# Control and following of the robot arm

## 1 Slider Control

Open a command line and run:

- mecharm 270-M5 version:

```bash
# The default serial port name of the mechArm 270-M5 version is "/dev/ttyUSB0", and the baud rate is 115200".
ros2 launch mecharm slider_control.launch.py
```

- mecharm 270-PI version:
  
Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower column of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-10.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-11.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-12.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of the mechArm 270-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
ros2 launch mecharm_pi slider_control.launch.py
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src =../../../resourse/12-ApplicationBaseROS/slider_control.png
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. The real mechArm will move with it.




**Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm.**

## 2 Model Following

In addition to the above controls, we can also let the model move by following the real robot arm. Open a command line and run:

- mecharm 270-M5 version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyUSB0", and the baud rate is 115200".
ros2 launch mecharm mycobot_follow.launch.py
```

- mecharm 270-PI version:
  
Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower column of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-10.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-11.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-12.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of the mechArm 270-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
ros2 launch mecharm_pi mycobot_follow.launch.py
```

It will **open rviz to show the model following effect.**



## 3 GUI control

On the basis of the previous contents, this package also **provides a simple GUI control interface.** This method is used for interaction between real robot arms. Connect to mecharm.

- mecharm 270-M5 version:

Open a command line:

```bash
# The default serial port name of the mechArm 270-M5 version is "/dev/ttyUSB0", and the baud rate is 115200".
ros2 launch mecharm simple_gui.launch.py
```

- mecharm 270-PI version:
  
Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower column of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-10.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-11.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-12.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of the mechArm 270-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
ros2 launch mecharm_pi simple_gui.launch.py
```

Running effect:

<img src =../../../resourse/12-ApplicationBaseROS/mecharm_gui.png
width ="500"  align = "center">

## 4 Keyboard control

**Keyboard control is added** in `mecharm` package, and real-time Synchronization is performed in rviz. This function depends on pythonApi, so be sure to connect with the real robot arm.



Open a command line and run:

- mecharm 270-M5 version:

```bash
# The default serial port name of the mechArm 270-PI version is "/dev/ttyUSB0", and the baud rate is 115200".
ros2 launch mecharm teleop_keyboard.launch.py
```

- mecharm 270-PI version:
  
Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower column of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-10.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-11.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-12.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of the mechArm 270-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
ros2 launch mecharm_pi teleop_keyboard.launch.py
```

Running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/mecharm_teleop.png
width ="500"  align = "center">

mechArm information will be output in the command line as follows:
```bash
[INFO] [launch]: All log files can be found below /home/u20/.ros/log/2022-08-01-14-53-35-880311-u20-VirtualBox-5591
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [robot_state_publisher-1]: process started with pid [5594]
[INFO] [rviz2-2]: process started with pid [5596]
[INFO] [follow_display-3]: process started with pid [5598]
[robot_state_publisher-1] Parsing robot urdf xml string.
[robot_state_publisher-1] Link link1 had 1 children
[robot_state_publisher-1] Link link2 had 1 children
[robot_state_publisher-1] Link link3 had 1 children
[robot_state_publisher-1] Link link4 had 1 children
[robot_state_publisher-1] Link link5 had 0 children
[robot_state_publisher-1] [INFO] [1659336816.100317312] [robot_state_publisher]: got segment base
[robot_state_publisher-1] [INFO] [1659336816.100434612] [robot_state_publisher]: got segment link1
[robot_state_publisher-1] [INFO] [1659336816.100443491] [robot_state_publisher]: got segment link2
[robot_state_publisher-1] [INFO] [1659336816.100451008] [robot_state_publisher]: got segment link3
[robot_state_publisher-1] [INFO] [1659336816.100457862] [robot_state_publisher]: got segment link4
[robot_state_publisher-1] [INFO] [1659336816.100464597] [robot_state_publisher]: got segment link5
[rviz2-2] [INFO] [1659336816.529758865] [rviz2]: Stereo is NOT SUPPORTED
[rviz2-2] [INFO] [1659336816.530082788] [rviz2]: OpenGl version: 3.1 (GLSL 1.4)
[rviz2-2] [INFO] [1659336816.620671305] [rviz2]: Stereo is NOT SUPPORTED
[follow_display-3] [INFO] [1659336816.635957580] [follow_display]: port:/dev/ttyUSB0, baud:115200
[rviz2-2] Parsing robot urdf xml string.
```


Then open another command line and run:

- mecharm 270-M5 version:

```bash
ros2 run mecharm teleop_keyboard
```

- mecharm 270-PI version:

Click the `ROS2 Shell` icon on the desktop or the corresponding icon in the lower column of the desktop to open the ROS2 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-10.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-11.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-12.jpg
width ="500"  align = "center">

Then run the command:

```bash
ros2 run mecharm_pi teleop_keyboard
```

You will see the following output in the command line:

```bash
mecharm Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx,ry,rz]):
              w(x+)

    a(y-)     s(x-)     d(y+)

        z(z-)       x(z+)

u(rx+)      i(ry+)      o(rz+)
j(rx-)      k(ry-)      l(rz-)

Gripper control:
    g - open
    h - close

Other:
    1 - Go to init pose
    2 - Go to home pose
    3 - Resave home pose
    q - Quit

currently:	speed: 40	change percent: 5  
```

Parameters supported by this script:

 * _speed: the movement speed of the robot arm
 * _change_percent: movement distance percentage
