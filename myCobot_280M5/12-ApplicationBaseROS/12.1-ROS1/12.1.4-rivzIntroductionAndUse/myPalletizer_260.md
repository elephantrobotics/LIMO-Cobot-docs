# Control and following of the robot arm
## 1 Slider Control

Open a command line and run:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mypalletizer_260 slider_control.launch port:=/dev/ttyUSB0 baud:=115200
```

- mypalletzier 260-Pi version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mypalletizer_260_pi slider_control.launch port:=/dev/ttyAMA0 baud:=1000000
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src =../../../resourse/12-ApplicationBaseROS/mypal260/260slider.png
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. If you want the real mycobot to move with the model, you need to open another command line and run:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mypalletizer_260 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

- mypalletzier 260-Pi version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mypalletizer_260_pi slider_control.py _port:=/dev/ttyAMA0 _baud:=1000000
```




**Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm.**

## 2 Model Following

In addition to the above controls, we can also let the model move by following the real robot arm. Open a command line and run:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mypalletizer_260 follow_display.py _port:=/dev/ttyUSB0 _baud:=115200
```

- mypalletzier 260-Pi version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mypalletizer_260_pi follow_display.py _port:=/dev/ttyAMA0 _baud:=1000000
```


Then open another command line and run:

- mypalletizer 260-M5 version:

```bash
roslaunch mypalletizer_260 follow.launch
```

- mypalletzier 260-Pi version:

```bash
roslaunch mypalletizer_260_pi follow.launch
```

It will **open rviz to show the model following effect.**



## 3 GUI control

On the basis of the previous contents, this package also **provides a simple GUI control interface.** This method is used for interaction between real robot arms. Connect to mycobot.

Open a command line:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mypalletizer_260 simple_gui.launch port:=/dev/ttyUSB0 baud:=115200
```

- mypalletzier 260-Pi version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mypalletizer_260_pi simple_gui.launch port:=/dev/ttyAMA0 baud:=1000000
```

Running effect:
<img src =../../../resourse/12-ApplicationBaseROS/mypal260/260GUI.png
width ="500"  align = "center">

## 4 Keyboard control

**Keyboard control is added** in `mypalletizer_260` package, and real-time Synchronization is performed in rviz. This function depends on pythonApi, so be sure to connect with the real robot arm.

Open a command line and run:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mypalletizer_260 teleop_keyboard.launch port:=/dev/ttyUSB0 baud:=115200
```

- mypalletzier 260-Pi version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
roslaunch mypalletizer_260_pi teleop_keyboard.launch port:=/dev/ttyAMA0 baud:=1000000
```


Running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/mypal260/260teleboard.png
width ="500"  align = "center">

mypalletizer information will be output in the command line as follows:

```bash
SUMMARY
========

PARAMETERS
 * /mypalletizer_services/baud: 125200
 * /mypalletizer_services/port: /dev/ttyUSB0
 * /robot_description: <?xml version="1....
 * /rosdistro: kinetic
 * /rosversion: 1.12.17

NODES
  /
    mypalletizer_services (mypalletizer_communication/mypal_services.py)
    real_listener (mypalletizer_260/listen_real.py)
    robot_state_publisher (robot_state_publisher/robot_state_publisher)
    rviz (rviz/rviz)

ROS_MASTER_URI=http://localhost:12312

process[robot_state_publisher-1]: started with pid [14764]
process[rviz-2]: started with pid [14765]
process[mypalletizer_services-3]: started with pid [14766]
process[real_listener-4]: started with pid [14782]
[INFO] [1646649869.148017]: start ...
[INFO] [1646649869.156531]: /dev/ttyUSB0,125200

Mypalletizer Status
--------------------------------
Joint Limit:
    joint 1: -160 ~ +160
    joint 2: 0 ~ +90
    joint 3: 0 ~ +60
    joint 4: -180 ~ +180
 

Connect Status: True

Servo Infomation: unknown

Servo Temperature: unknown

Atom Version: unknown

[INFO] [1646649869.427899]: ready
```


Then open another command line and run:

- mypalletizer 260-M5 version:

```bash
rosrun mypalletizer_260 teleop_keyboard.py
# or
rosrun mypalletizer_260 teleop_keyboard.py _speed:=70
```

- mypalletizer 260-Pi version:

```bash
rosrun mypalletizer_260_pi teleop_keyboard.py
# or
rosrun mypalletizer_260 teleop_keyboard.py _speep:70
```

You will see the following output in the command line:

```bash
Mypalletizer Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx]):
              w(x+)

    a(y-)     s(x-)     d(y+)

        z(z-)       x(z+)

        u(rx+)      i(rx-)
   

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
In this terminal, you can control the state of the robot arm and move it using the keys in the command line.

Parameters supported by this script:

 * _speed: the movement speed of the robot arm
 * _change_percent: movement distance percentage
