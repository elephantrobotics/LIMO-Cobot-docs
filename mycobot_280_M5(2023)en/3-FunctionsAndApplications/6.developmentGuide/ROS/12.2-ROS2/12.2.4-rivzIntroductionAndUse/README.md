# A brief introduction and use of rviz2

rviz is a three-dimensional visualization platform in ROS. On the one hand, it can realize the graphical display of external information. On the other hand, it can also release control information to objects through rviz, thereby realizing the monitoring and control of robots.

## Introduction to rviz2

The successful installation of ros2 indicates that rviz2 is also successfully installed, because the installation of ros2 includes rviz2.

Open a new terminal (shortcut <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the command to open rviz2

```bash
rviz2
```

Open rviz2 and the following interface will be displayed:

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz-1.png
width ="500" align = "center">

## Introduction to each area

+ On the left is the display list. The display is something that draws something in the 3D world and may have some options available in the display list.

+ Above is the toolbar, which allows the user to select multiple functions with various function keys

+ The middle part is the 3D view: it is the main screen for viewing various data in three dimensions. The background color, fixed frame, grid, etc. of the 3D view can be set in detail in the Global Options and Grid items displayed on the left.
+ Below is the time display area, including system time and ROS time.
+ On the right is the observation angle setting area, where different observation angles can be set.

In this section, we only give a rough introduction. If you want to know more details, you can go to the [User Guide](http://wiki.ros.org/rviz/UserGuide) to check it out.

## mycobot_ros2 installation and update

- **M5 version:** Please check the end of the [12.2.1 ROS2 installation](../12.2.1-ROS2 installation.md) section.

## Simple use

**Start through the launch.py ​​file**

This example is based on the fact that you have completed [Environment Setup](../12.2.1-ROS2 Installation.md) and successfully copied the company's code from GitHub.

Open a console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>)
Enter the following command to **ROS2 environment configuration**.

```
cd ~/colcon_ws
colcon build --symlink-install
source install/setup.bash
```

Enter again:

- mycobot 280-M5 version:

```bash
ros2 launch mycobot_280 test.launch.py
```

![image-20220519154315585](../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/ros2_open1.png)

Open rviz2 and get the following result:

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/open-2.png
width ="500" align = "center">

If you want to learn more about rviz, you can go to the [official document](http://wiki.ros.org/rviz2) to view it

## M5 version prerequisites

- Open the console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>), open the terminal window to view the device name:

```bash
# View the device name of the robot arm
ls /dev/ttyUSB* # Old version myCobot280 M5

# If the terminal does not display the /dev/ttyUSB related name, you need to use the following command
ls /dev/ttyACM* # New version myCobot280 M5
```

- Grant serial port permissions to the robot:

```bash
# The default device name is /dev/ttyUSB0. If the device name is not the default value, you need to modify it.
sudo chmod 777 /dev/ttyUSB0 # Old version myCobot280 M5

sudo chmod 777 /dev/ttyACM0 # New version myCobot280 M5
```

Then enter the user password (**Note:** The password is not displayed, just enter it correctly).

# 280 series rviz user guide

## Robot arm control

### Slider control

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 slider_control.launch.py port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/caf-1.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider**. The real mycobot will move with it.

**Please note: Since the robot arm will move to the current position of the model when the command is entered, please make sure that the model in rviz does not appear to be through the model before you use the command**
**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**

### Model following

In addition to the above control, we can also **let the model follow the movement of the real robot arm**. Open a command line and run:

- mycobot 280-M5 version:
##### Slider control

> **Note: This function only supports the control of the robot**

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, the serial port name can be changed to "/dev/ttyACM0".
ros2 launch mycobot_280 slider_control_pump.launch.py port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280//12.1.4-16.png
width ="500" align = "center">

Then you can **control the model movement in rviz by dragging the slider**. The real mycobot will move with it.

**Please note: Since the robot arm will move to the current position of the model when the command is input, please make sure that the model in rviz does not appear to be through the model before you use the command**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**

### GUI control

Based on the previous, this package also **provides a simple Gui control interface**. This method is intended to allow real robotic arms to interact with each other. Please connect mycobot.

Open the command line:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 simple_gui.launch.py port:=/dev/ttyUSB0 baud:=115200
```

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/gui-1.png
width ="500" align = "center">

### Keyboard control

**Keyboard control function has been added to the `mycobot_280` package**, and it is synchronized in real time in rviz. This function relies on pythonApi, so make sure it is connected to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 teleop_keyboard.launch.py port:=/dev/ttyUSB0 baud:=115200
```

Then run the command:

```
[INFO] [launch]: All log files can be found below /home/elephant/.ros/log/2022-05-19-16-25-45-949761-elephant-virtual-machine-19111
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [robot_state_publisher-1]: process started with pid [19114]
[INFO] [rviz2-2]: process started with pid [19116]
[INFO] [follow_display-3]: process started with pid [19118]
[robot_state_publisher-1] Parsing robot urdf xml string.
[robot_state_publisher-1] Link joint2 had 1 children
[robot_state_publisher-1] Link joint3 had 1 children
[robot_state_publisher-1] Link joint4 had 1 children
[robot_state_publisher-1] Link joint5 had 1 children
[robot_state_publisher-1] Link joint6 had 1 children
[robot_state_publisher-1] Link joint6_flange had 0 children
[robot_state_publisher-1] [INFO] [1652948746.290904045] [robot_state_publisher]: got segment joint1
[robot_state_publisher-1] [INFO] [1652948746.290967253] [robot_state_publisher]: got segment joint2
[robot_state_publisher-1] [INFO] [1652948746.290973124] [robot_state_publisher]: got segment joint3
[robot_state_publisher-1] [INFO] [1652948746.290977490] [robot_state_publisher]: got segment joint4
[robot_state_publisher-1] [INFO] [1652948746.290981670] [robot_state_publisher]: got segment joint5
[robot_state_publisher-1] [INFO] [1652948746.290985737] [robot_state_publisher]: got segment joint6
[robot_state_publisher-1] [INFO] [1652948746.290989943] [robot_state_publisher]: got segment joint6_flange
[follow_display-3] [INFO] [1652948746.664601707] [follow_display]: port:/dev/ttyUSB0, baud:115200
[rviz2-2] [INFO] [1652948746.828773551] [rviz2]: Stereo is NOT SUPPORTED
[rviz2-2] [INFO] [1652948746.830452458] [rviz2]: OpenGl version: 4.1 (GLSL 4.1)
[rviz2-2] [INFO] [1652948746.874021926] [rviz2]: Stereo is NOT SUPPORTED
[rviz2-2] Parsing robot urdf xml string.
```

The running effect is as follows:

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/kb-1.png
width ="500" align = "center"> Mycobot information will be output on the command line, as follows: 

```bash [INFO] [launch]: All log files can be found below /home/elephant/.ros/log/2022-05-19-16-25-45-949761-elephant-virtual-machine-19111 [INFO] [launch]: Default logging verbosity is set to INFO [INFO] [robot_state _publisher-1]: process started with pid [19114] [INFO] [rviz2-2]: process started with pid [19116] [INFO] [follow_display-3]: process started with pid [19118] [robot_state_publisher-1] Parsing robot urdf XML string. children [robot_state_publisher-1] Link joint3 had 1 children [robot_state_publisher-1] Link joint4 had 1 children [robot_state_publisher-1] Link joint5 had 1 children [robot_state_publisher-1] Link joint6 had 1 children [robot_state_publisher-1] Link joint6_flange had 0 children [robot_state_publisher-1] [INFO] [ 1652948746.290904045] [robot_state_publisher]: got segment joint1 [robot_state_publisher-1] [INFO] [1652948746.290967253] [robot_state_publisher]: got segment joint2 [robot_state_publisher-1] [INFO] [1652948746.290973124] [robot_state_publisher]: got segment joint3 [robot_state_publisher-1] [INFO] [1652948746.290977490] [robot_state_publisher]: got segment joint4 [robot_state_publisher-1] [INFO] [1652948746.2 90981670] [robot_state_publisher]: got segment joint5 [robot_state_publisher-1] [INFO] [1652948746.290985737] [robot_state_publisher]: got segment joint6 [robot_state_publisher-1] [INFO] [1652948746.290989943] [robot_state_publisher]: got segment joint6_flange [follow_display-3] [INFO] [1652948746.664601707] [follow_display]: port:/dev/ttyUSB0, baud:115200
[rviz2-2] [INFO] [1652948746.828773551] [rviz2]: Stereo is NOT SUPPORTED
[rviz2-2] [INFO] [1652948746.830452458] [rviz2]: OpenGl version: 4.1 (GLSL 4.1)
[rviz2-2] [INFO] [1652948746.874021926] [rviz2]: Stereo is NOT SUPPORTED
[rviz2-2] Parsing robot urdf xml string.
```

You will see the following output in the command line:
```bash
Mycobot Teleop Keyboard Controller
---------------------------
Movimg options(control coordinations [x,y,z,rx,ry,rz]):
w(x+)

a(y-) s(x-) d(y+)

z(z-) x(z+)

u(rx+) i(ry+) o(rz+)

j(rx-) k(ry-) l(rz-)

Gripper control:
g - open
h - close

Other:
1 - Go to init pose
2 - Go to home pose
3 - Resave home pose
q - Quit

currently: speed: 10 change percent: 2
```

In this terminal, you can control the state of the robot and move the robot by pressing keys in the command line.

### End effector

- **Supported end effectors:** myCobot vertical suction pump V2.0, camera flange

- **Applicable devices:** myCobot 280 M5, myCobot 280 PI

#### myCobot vertical suction pump V2.0

##### 1 Load the model

Open a command line and run:

- mycobot 280-M5 version:

```bash
ros2 launch mycobot_280 test_pump.launch.py
```

It will **open rviz**, and you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/12.1.4-13.png
width ="500" align = "center">

##### 2 Slider control

> **Note: This function only supports the control of the robot arm**

Open a command line and run:

- mycobot 280-M5 version:

```bash
# mycobot The default serial port name of the 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 slider_control_pump.launch.py port:=/dev/ttyUSB0 baud:=115200
```

It will open rviz and a slider component, you will see the following screen (the Raspberry Pi version screen is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/12.1.4-16.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider**. The real mycobot will move with it.

**Please note: Since the robot arm will move to the current position of the model while the command is input, please make sure that the model in rviz does not appear to be through the model before you use the command**
**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**

##### 3 GUI control

Based on the previous, this package also **provides a simple Gui control interface**. This method is intended for real robot arms to be linked to each other. Please connect mycobot.

Open the command line:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 simple_gui_pump.launch.py port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a GUI interface**, and you will see the following screen:

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280/12.1.4-14.png
width ="500" align = "center">

#### Camera flange

##### 1 Load the model

Open a command line and run:

- mycobot 280-M5 version:

```bash
ros2 launch mycobot_280 test_camera_flange.launch.py
```

It will **open rviz**, you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280//12.1.4-15.png
width ="500" align = "center">

##### 2 Slider control

> **Note: This function only supports the control of the robot arm**

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of the mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0", if the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
ros2 launch mycobot_280 slider_control_camera_flange.launch.py port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280//12.1.4-17.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider**. The real mycobot will move with it.

**Please note: Since the robot arm will move to the current position of the model when the command is entered, please make sure that the model in rviz does not appear to be through the model before you use the command**.
**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**.

#### Camera flange && pump

##### 1 Load the model

Open a command line and run:

- mycobot 280-M5 version:

```bash
ros2 launch mycobot_280 test_camera_flange_pump.launch.py
```

It will **open rviz**, you will see the following screen (the screen of the Raspberry Pi version is slightly different, which does not affect the use):

<img src =../.../../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/rviz2/rviz2-280//12.1.4-18.png
width ="500" align = "center">

#### URDF model address

##### 1 myCobot vertical suction pump V2.0

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros2/blob/280-ros-pump-camera/mycobot_description/urdf/mycobot/mycobot_with_pump.urdf)

##### 2 Camera flange

- [myCobot 280-M5 Version](https://github.com/elephantrobotics/mycobot_ros2/tree/humble/mycobot_description/urdf/mycobot/mycobot_with_camera_flange.urdf)

##### 3 Camera Flange && Pump

- [myCobot 280-M5 Version](https://github.com/elephantrobotics/mycobot_ros2/tree/humble/mycobot_description/urdf/mycobot/mycobot_with_camera_flange_pump.urdf)