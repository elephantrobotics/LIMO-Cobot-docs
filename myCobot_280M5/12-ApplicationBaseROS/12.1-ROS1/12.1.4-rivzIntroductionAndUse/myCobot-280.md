# Control and following of the robot arm

## 1 Slider Control

Open a command line and run:

- mycobot 280-M5 version：
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 slider_control.launch port:=/dev/ttyUSB0 baud:=115200
```

- mycobot 280-Pi version：
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280pi slider_control.launch port:=/dev/ttyAMA0 baud:=1000000
```

- mycobot 280-JetsonNano version：
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
roslaunch mycobot_280jn slider_control.launch port:=/dev/ttyTHS1 baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
roslaunch mycobot_280arduino slider_control.launch port:=/dev/ttyACM0 baud:=115200
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src =../../../resourse/12-ApplicationBaseROS/caf-1.png
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. If you want the real mycobot to move with the model, you need to open another command line and run:

- mycobot 280-M5 version：
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

- mycobot 280-Pi version：
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
rosrun mycobot_280pi slider_control.py _port:=/dev/ttyAMA0 _baud:=1000000
```

- mycobot 280-JetsonNano version：
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
rosrun mycobot_280jn slider_control.py _port:=/dev/ttyTHS1 _baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
rosrun mycobot_280arduino slider_control.py _port:=/dev/ttyACM0 _baud:=115200
```




Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm.

## 2 Model Following

In addition to the above controls, we can also let the model move by following the real robot arm. Open a command line and run:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 follow_display.py _port:=/dev/ttyUSB0 _baud:=115200
```

- mycobot 280-pi version:
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
rosrun mycobot_280pi follow_display.py _port:=/dev/ttyAMA0 _baud:=1000000
```

- mycobot 280-JetsonNano version:
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
rosrun mycobot_280jn follow_display.py _port:=/dev/ttyTHS1 _baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
rosrun mycobot_280arduino follow_display.py _port:=/dev/ttyACM0 _baud:=115200
```



Then open another command line and run:


- mycobot 280-M5 version:
  
```bash
roslaunch mycobot_280 mycobot_follow.launch
```

- mycobot 280-Pi version:
  
```bash
roslaunch mycobot_280pi mycobot_follow.launch
```

- mycobot 280-JetsonNano version:
  
```bash
roslaunch mycobot_280jn mycobot_follow.launch
```

- mycobot 280-Arduino version：
  
```bash
roslaunch mycobot_280arduino mycobot_follow.launch
```

It will **open rviz to show the model following effect.**


## 3 GUI control

On the basis of the previous contents, this package also **provides a simple GUI control interface.** This method is used for interaction between real robot arms. Connect to mycobot.

Open a command line:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 simple_gui.launch port:=/dev/ttyUSB0 baud:=115200
```

- mycobot 280-Pi version:
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280pi simple_gui.launch port:=/dev/ttyAMA0 baud:=1000000
```

- mycobot 280-JetsonNano version:
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
roslaunch mycobot_280jn simple_gui.launch port:=/dev/ttyTHS1 baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
roslaunch mycobot_280arduino simple_gui.launch port:=/dev/ttyACM0 baud:=115200
```

Running effect:

<img src =../../../resourse/12-ApplicationBaseROS/gui-1.png
width ="500"  align = "center">

## 4 Keyboard control

**Keyboard control is added** in `mycobot_280` package, and real-time Synchronization is performed in rviz. This function depends on pythonApi, so be sure to connect with the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard.launch port:=/dev/ttyUSB0 baud:=115200
```

- mycobot 280-Pi version:
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280pi teleop_keyboard.launch port:=/dev/ttyAMA0 baud:=1000000
```

- mycobot 280-JetsonNano version:
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
roslaunch mycobot_280jn teleop_keyboard.launch port:=/dev/ttyTHS1 baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
roslaunch mycobot_280arduino teleop_keyboard.launch port:=/dev/ttyACM0 baud:=115200
```


Running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/kb-1.png
width ="500"  align = "center">

mycobot information will be output in the command line as follows:

```bash
SUMMARY
========

PARAMETERS
 * /mycobot_services/baud: 115200
 * /mycobot_services/port: /dev/ttyUSB0 or /dev/ttyAMA0
 * /robot_description: <?xml version="1....
 * /rosdistro: kinetic
 * /rosversion: 1.12.17

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


Then open another command line and run:


- mycobot 280-M5 verion:

```bash
rosrun mycobot_280 teleop_keyboard.py
#or
rosrun mycobot_280 teleop_keyboard.py _speed:=70
```

- mycobot 280-Pi version:

```bash
rosrun mycobot_280 teleop_keyboard.py
#or
rosrun mycobot_280pi teleop_keyboard.py _speed:=70
```

- mycobot 280-JetsonNano version:

```bash
rosrun mycobot_280jn teleop_keyboard.py
#or
rosrun mycobot_280jn teleop_keyboard.py _speed:=70
```

- mycobot 280-Arduino version:

```bash
rosrun mycobot_280arduino teleop_keyboard.py
#or
rosrun mycobot_280arduino teleop_keyboard.py _speed:=70
```



You will see the following output in the command line:

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

In this terminal, you can control the state of the robot arm and move it using the keys in the command line.

Parameters supported by this script:

 * _speed: the movement speed of the robot arm
 * _change_percent: movement distance percentage





## 5 Vision

>Install the camera at the end of the mycobot. This visual section uses an eye-in-hand method.

<img src =../../../resourse/13-AdvancedKit/camera_connect-1.jpg
width ="500"  align = "center">

### 5.1 Identification and display

Run in the command line:

- mycobot 280-M5 version:
  
```bash
roslaunch mycobot_280 detect_marker.launch
```

- mycobot 280-Pi version:
  
```bash
roslaunch mycobot_280pi detect_marker.launch
```

- mycobot 280-JetsonNano version:
  
```bash
roslaunch mycobot_280jn detect_marker.launch
```

- mycobot 280-Arduino version:
  
```bash
roslaunch mycobot_280arduino detect_marker.launch
```

Optional parameters:

+ num: camera id; the default is 0.

Rendering after startup:

<img src =../../../resourse/12-ApplicationBaseROS/vision-1.png
width ="500"  align = "center">

Identify the QR code and obtain the relative position relationship with the camera. According to the end position of mycobot in rviz, do coordinate transformation, and is finally displayed in rviz.

You may refer to [slider control](##1421-滑块控制), and use `slider_control.py` to control the robot arm.


### 5.2 Visual Tracking and Grabbing

>This section requires the use of a vertical adsorption pump.

Run in the command line:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 detect_marker_with_topic.launch port:=/dev/ttyUSB0 baud:=115200
```

- mycobot 280-Pi version:
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280 detect_marker_with_topic.launch port:=/dev/ttyAMA0 baud:=1000000
```

- mycobot 280-JetsonNano version:
  
```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
roslaunch mycobot_280jn detect_marker_with_topic.launch port:=/dev/ttyTHS1 baud:=1000000
```

- mycobot 280-Arduino version：
  
```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
roslaunch mycobot_280arduino detect_marker_with_topic.launch port:=/dev/ttyACM0 baud:=115200
```

Optional parameters:

+ num: camera id; the default is 0.
+ port: serial port string
+ baud: baud rate


Rendering after startup:

The state of mycobot will be displayed in reat time.

<img src =../../../resourse/12-ApplicationBaseROS/vision-2.gif
width ="500"  align = "center">

Then run the script tracked and scraped. Open a new command line:

- mycobot 280-M5 version:
  
```bash
rosrun mycobot_280 follow_and_pump.py
```

- mycobot 280-Pi version:
  
```bash
rosrun mycobot_280pi follow_and_pump.py
```

- mycobot 280-JetsonNano version:
  
```bash
rosrun mycobot_280jn follow_and_pump.py
```

- mycobot 280-Arduino version:
  
```bash
rosrun mycobot_280arduino follow_and_pump.py
```


After startup, mycobot will go to its initial position.

<img src =../../../resourse/12-ApplicationBaseROS/vision-3.gif
width ="500"  align = "center">

When a marker is recognized, follow it for a while, then try to pick up and end the program.

<img src =../../../resourse/12-ApplicationBaseROS/vision-4.png
width ="500"  align = "center">

## 6 End Effector

- **Supported end effectors：** myCobot adaptive gripper, myCobot vertical suction pump V2.0, camera flange

- **Applicable devices:** myCobot 280 M5、myCobot 280 PI

> Note: myCobot adaptive gripper only supports myCobot 280 M5 device

### 6.1 myCobot adaptive gripper

#### 1 Load model

Open a command line and run:

- myCobot 280-M5 version：

```bash
roslaunch mycobot_280 test_gripper.launch
```

It will **open rviz** and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-10.png
width ="500"  align = "center">

#### 2 Slider Control

Open a command line and run:

- myCobot 280-M5 version：

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
roslaunch mycobot_280 slider_control_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see something like this:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-11.png
width ="500"  align = "center">

You can then control the model movement in rviz by dragging the slider. ** If you want the real myCobot to move along with you, you need to **open another command line** and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
rosrun mycobot_280 slider_control_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```

**Please note: Since the robot arm will move to the current position of the model when the command is entered, please make sure that the model in rviz does not have mold penetration before you use the command**.
**Do not quickly drag the slider after connecting the robotic arm to prevent damage to the robotic arm**.

#### 3 Model Follows

In addition to the above controls, we can also make the model follow the movement of the real robotic arm. Open a command line and run:

- mycobot 280-M5 version：
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
rosrun mycobot_280 follow_display_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```

Then open another command line and run:

- mycobot 280-M5 version:
  
```bash
roslaunch mycobot_280 mycobot_follow_gripper.launch
```

It will open rviz to display the model following effect.

#### 4 GUI Control

On the basis of the previous ones, this package also provides a simple Gui control interface. This method is intended for real robot arms to interact with each other, please connect to myCobot.

Open the command line:

- mycobot 280-M5 version：
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 simple_gui_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a GUI interface**, and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-12.png
width ="500"  align = "center">

#### 5 Keyboard Control

The keyboard control function has been added to the `mycobot_280` package and synchronized in real time in rviz. This function relies on pythonApi, so make sure it is connected to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

The running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-10.png
width ="500"  align = "center">

myCobot information will be output on the command line, as follows:

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

Next, open another command line and run:

- mycobot 280-M5 version:

```bash
rosrun mycobot_280 teleop_keyboard.py
```

You will see the following output on the command line:

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

In this terminal, you can control the status of the robotic arm and move the robotic arm through the keys on the command line.

Parameters supported by this script:

+ _speed: Robot arm moving speed.
+ _change_percent: Percentage of moving distance.

### 6.2 myCobot vertical suction pump V2.0

#### 1 Load model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_pump.launch
```

- myCobot 280-PI version:

```bash
roslaunch mycobot_280pi test_pump.launch
```

It will **open rviz** and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-13.png
width ="500"  align = "center">

#### 2 Slider Control

> **Note: This function only supports control of the robotic arm**

Open a command line and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 slider_control_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

- myCobot 280-PI version：

```bash
# The default serial port name of myCobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280pi slider_control_pump.launch port:=/dev/ttyAMA0 baud:=1000000
```

It will open rviz and a slider component, and you will see something like this:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-16.png
width ="500"  align = "center">

You can then control the model movement in rviz by dragging the slider. ** If you want the real myCobot to move along with you, you need to **open another command line** and run:

- myCobot 280-M5 version：

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

- myCobot 280-PI version：

```bash
# The default serial port name of myCobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
rosrun mycobot_280pi slider_control.py _port:=/dev/ttyAMA0 _baud:=1000000
```

**Please note: Since the robot arm will move to the current position of the model when the command is entered, please make sure that the model in rviz does not have mold penetration before you use the command**.
**Do not quickly drag the slider after connecting the robotic arm to prevent damage to the robotic arm**.

#### 3 GUI control

On the basis of the previous ones, **this package also provides a simple Gui control interface**. This method is intended for real robot arms to interact with each other, please connect to myCobot.

Open the command line:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 simple_gui_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a GUI interface**, and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-14.png
width ="500"  align = "center">

#### 4 Keyboard Control

**The keyboard control function has been added** to the `mycobot_280` package and synchronized in real time in rviz. This function relies on python API, so make sure it is connected to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

The running effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-13.png
width ="500"  align = "center">

Next, open another command line and run:

- mycobot 280-M5 version:

```bash
rosrun mycobot_280 teleop_keyboard.py
```

You will see the following output on the command line:

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

In this terminal, you can control the status of the robotic arm and move the robotic arm through the keys on the command line.

Parameters supported by this script:

+ _speed: Robot arm moving speed.
+ _change_percent: Percentage of moving distance.

### 6.3 Camera Flange

#### 1 Load model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_camera_flange.launch
```

- myCobot 280-PI version:

```bash
roslaunch mycobot_280pi test_camera_flange.launch
```

It will **open rviz** and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-15.png
width ="500"  align = "center">

#### 2 Slider Control

> **Note: This function only supports control of the robotic arm**

Open a command line and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
roslaunch mycobot_280 slider_control_camera_flange.launch port:=/dev/ttyUSB0 baud:=115200
```

- myCobot 280-PI version：

```bash
# The default serial port name of myCobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
roslaunch mycobot_280pi slider_control_camera_flange.launch port:=/dev/ttyAMA0 baud:=1000000
```

It will open rviz and a slider component, and you will see something like this:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-17.png
width ="500"  align = "center">

You can then control the model movement in rviz by dragging the slider. **If you want the real myCobot to move along** with you, you need to **open another command line** and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to " /dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

- myCobot 280-PI version：

```bash
# The default serial port name of myCobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
rosrun mycobot_280pi slider_control.py _port:=/dev/ttyAMA0 _baud:=1000000
```

**Please note: Since the robot arm will move to the current position of the model when the command is entered, please make sure that the model in rviz does not have mold penetration before you use the command**.
**Do not quickly drag the slider after connecting the robotic arm to prevent damage to the robotic arm**.

### 6.4 Camera Flange && pump

#### 1 Load model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_camera_flange_pump.launch
```

- myCobot 280-PI version:

```bash
roslaunch mycobot_280pi test_camera_flange_pump.launch
```

It will **open rviz** and you will see the following screen:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-18.png
width ="500"  align = "center">

### 6.5 URDF Model Address

#### 1 myCobot Adaptable Gripper

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/blob/280-ros-pump-camera/mycobot_description/urdf/mycobot/mycobot_with_gripper_parallel.urdf)

#### 2 myCobot Vertical Suction Pump V2.0

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_pump.urdf)

- [myCobot 280-PI version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot_pi/mycobot_with_pump.urdf)
  
#### 3 Camera Flange

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange.urdf)

- [myCobot 280-PI version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot_pi/mycobot_with_camera_flange.urdf)
  
#### 4 Camera Flange && pump

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange_pump.urdf)

- [myCobot 280-PI version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot_pi/mycobot_with_camera_flange_pump.urdf)
  