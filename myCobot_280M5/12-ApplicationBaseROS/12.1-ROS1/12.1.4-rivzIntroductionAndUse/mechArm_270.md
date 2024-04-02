# Control and following of the robot arm

## 1 Slider Control

Open a command line and run:

mechArm-M5 version：

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
roslaunch mecharm slider_control.launch port:=/dev/ttyUSB0 baud:=115200
```

mechArm-PI version：

```bash
# The default serial port name of the mechArm-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mecharm_pi slider_control.launch port:=/dev/ttyAMA0 baud:=1000000
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src =../../../resourse/12-ApplicationBaseROS/slider_control.png
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. If you want the real mechArm to move with the model, you need to open another command line and run:

mechArm-M5 version：

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
rosrun mecharm slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

mechArm-PI version：

```bash
# The default serial port name of the mechArm-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mecharm_pi slider_control.py _port:=/dev/ttyAMA0 _baud:=1000000
```



**Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm.**

## 2 Model Following

In addition to the above controls, we can also let the model move by following the real robot arm. Open a command line and run:

mechArm-M5 version：

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
rosrun mecharm follow_display.py _port:=/dev/ttyUSB0 _baud:=115200
```

mechArm-PI version：

```bash
# The default serial port name of the mechArm-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mecharm_pi follow_display.py _port:=/dev/ttyAMA0 _baud:=1000000
```

Then open another command line and run:

mechArm-M5 version：

```bash
roslaunch mecharm follow.launch
```

mechArm-PI version：

```bash
roslaunch mecharm_pi follow.launch
```

It will **open rviz to show the model following effect.**



## 3 GUI control

On the basis of the previous contents, this package also **provides a simple GUI control interface.** This method is used for interaction between real robot arms. Connect to mecharm.

Open a command line:

mechArm-M5 version：

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
roslaunch mecharm simple_gui.launch port:=/dev/ttyUSB0 baud:=115200
```

mechArm-PI version：

```bash
# The default serial port name of the mechArm-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mecharm_pi simple_gui.launch port:=/dev/ttyAMA0 baud:=1000000
```

Running effect:

<img src =../../../resourse/12-ApplicationBaseROS/mecharm_gui.png
width ="500"  align = "center">

## 4 Keyboard control

**Keyboard control is added** in `mecharm` package, and real-time Synchronization is performed in rviz. This function depends on pythonApi, so be sure to connect with the real robot arm.

Open a command line and run:

mechArm-M5 version：

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
roslaunch mecharm teleop_keyboard.launch port:=/dev/ttyUSB0 baud:=115200
```

mechArm-PI version：

```bash
# The default serial port name of the mechArm-PI version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mecharm_pi teleop_keyboard.launch port:=/dev/ttyAMA0 baud:=1000000
```


Running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/mecharm_teleop.png
width ="500"  align = "center">

mechArm information will be output in the command line as follows:

```bash
SUMMARY
========

PARAMETERS
 * /mecharm_services/baud: 1000000
 * /mecharm_services/port: /dev/ttyAMA0
 * /robot_description: <?xml version="1....
 * /rosdistro: melodic
 * /rosversion: 1.14.11

NODES
  /
    mecharm_services (mecharm_communication/mypal_services.py)
    real_listener (mecharm_pi/listen_real.py)
    robot_state_publisher (robot_state_publisher/robot_state_publisher)
    rviz (rviz/rviz)

ROS_MASTER_URI=http://localhost:11311

process[robot_state_publisher-1]: started with pid [14764]
process[rviz-2]: started with pid [14765]
process[mecharm_services-3]: started with pid [14766]
process[real_listener-4]: started with pid [14782]
[INFO] [1646649869.148017]: start ...
[INFO] [1646649869.156531]: /dev/ttyAMA0,1000000

Mycobot Status
--------------------------------
Joint Limit:
    joint 1: -160 ~ +160
    joint 2: -90 ~ +90
    joint 3: -180 ~ +45
    joint 4: -160 ~ +160
    joint 5: -100 ~ +100
    joint 6: -180 ~ +180

Connect Status: True

Servo Infomation: unknown

Servo Temperature: unknown

Atom Version: unknown

[INFO] [1646649869.427899]: ready
```


Then open another command line and run:


mechArm-M5 version：

```bash
rosrun mecharm teleop_keyboard.py
# or
rosrun mecharm teleop_keyboard.py _speed:=70
```

mechArm-PI version：

```bash
rosrun mecharm_pi teleop_keyboard.py
# or
rosrun mecharm_pi teleop_keyboard.py _speed:=70
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
