# Control and following of the robot arm

### 1 Slider Control

Click the `ROS1 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
roslaunch myarm slider_control.launch _port:=/dev/ttyAMA0 _baud:=115200
```

It will open rviz with a slider component and you will see something like this:

<img src =../../../resourse/12-ApplicationBaseROS/myarm_slider_control.png
width ="500"  align = "center">

Then you can control the movement of the model in rviz by dragging the slider. If you want the real myarm to move together, you need to open another ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
rosrun myarm slider_control.py _port:=/dev/ttyAMA0 _baud:=115200
```


**Please note: Since the robot arm will move to the current position of the model when the command is input, please make sure that the model in rviz does not have mold penetration before you use the command**
**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**

### 2 Model Following

In addition to the above controls, we can also make the model follow the real robot arm movement. Open a ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
rosrun myarm follow_display.py _port:=/dev/ttyAMA0 _baud:=115200
```

Then open another ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
roslaunch myarm mycobot_follow.launch
```

It will open rviz showing the model following effect.

<img src =../../../resourse/12-ApplicationBaseROS/myarm_follow.png
width ="500"  align = "center">


### 3 GUI Control

On the previous basis, this package also provides a simple GUI control interface. This method is intended to link real robotic arms with each other, please connect myArm-300.

Open a ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
roslaunch myarm simple_gui.launch port:=/dev/ttyAMA0 baud:=115200
```

running result:

<img src =../../../resourse/12-ApplicationBaseROS/myarm_gui.png
width ="500"  align = "center">

### 4 Keyboard Control

Added keyboard control function in `myarm` package, and real-time synchronization in rviz. This function relies on pythonAPI, so make sure to connect with a real robotic arm.

Open a ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
roslaunch myarm teleop_keyboard.launch port:=/dev/ttyAMA0 baud:=115200
```


The running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/myarm_follow.png
width ="500"  align = "center">

The myArm-300 information will be output on the command line, as follows:

```bash
SUMMARY
========

PARAMETERS
 * /myarm_services/baud: 115200
 * /myarm_services/port: /dev/ttyAMA0
 * /robot_description: <?xml version="1....
 * /rosdistro: noetic
 * /rosversion: 1.15.14

NODES
  /
    myarm_services (myarm_communication/myarm_services.py)
    real_listener (myarm/listen_real.py)
    robot_state_publisher (robot_state_publisher/robot_state_publisher)
    rviz (rviz/rviz)

ROS_MASTER_URI=http://localhost:11311

process[robot_state_publisher-1]: started with pid [14764]
process[rviz-2]: started with pid [14765]
process[mecharm_services-3]: started with pid [14766]
process[real_listener-4]: started with pid [14782]
[INFO] [1646649869.148017]: start ...
[INFO] [1646649869.156531]: /dev/ttyAMA0,115200

Mycobot Status
--------------------------------
Joint Limit:
    joint 1: -160 ~ +160
    joint 2: -80 ~ +80
    joint 3: -175 ~ +175
    joint 4: -100 ~ +80
    joint 5: -165 ~ +165
    joint 6: -110 ~ +110
    joint 7: -165 ~ +165

Connect Status: True

Servo Infomation: unknown

Servo Temperature: unknown

Atom Version: unknown

[INFO] [1646649869.427899]: ready
```

Then open another ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
rosrun myarm teleop_keyboard.py
```

You will see the following output on the command line:

```bash
myArm-300 Teleop Keyboard Controller
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

currently:	speed: 50	change percent: 5  
```

Parameters supported by this script:

+ _speed: The moving speed of the robotic arm.
+ _change_percent: Movement distance percentage.
