# A brief introduction and use of rviz

rviz is a 3D visualization platform in ROS. On the one hand, it can realize the graphical display of external information. On the other hand, it can also release control information to objects through rviz, thereby realizing the monitoring and control of robots.

## Introduction to the installation and interface of rviz

When installing ros, if you perform a complete installation, rviz has been installed, and you can try to run it directly; if it is not fully installed, you can install rviz separately:

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

After the installation is complete, please open a new terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the following command:
```bash
roscore
```

Then open a new terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the command to open rviz

```bash
rosrun rviz rviz
# or
rviz
```

Open rviz and the following interface will be displayed:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz-1.png
width ="500" align = "center">

### Introduction to each area

+ On the left is the display list. A display is something that draws something in the 3D world and may have some options available in the display list.

+ On the top is the toolbar, which allows users to select multiple functions with various function keys

+ In the middle is the 3D view: it is the main screen that allows users to view various data in three dimensions. The background color, fixed frame, grid, etc. of the 3D view can be set in detail in the Global Options and Grid items displayed on the left.

+ Below is the time display area, including system time and ROS time.

+ On the right is the observation angle setting area, which can set different observation angles.

In this section, we will only give a rough introduction. If you want to know more details, you can go to the [User Guide](http://wiki.ros.org/rviz/UserGuide) to check it out.

## mycobot_ros installation and update

- **M5 version:** Please see the end of the **ROS1 Environment Setup** section.

  ***

## Simple use

**Start through the launch file**

This example is based on the premise that you have completed [Environment Construction](../12.1.2-Environment Construction.md) and successfully copied the company's code from GitHub.

Open a console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>)
Enter the following command to **ROS environment configuration**.

```bash
cd ~/catkin_ws/
source devel/setup.bash
```

Enter again:

- mycobot 280-M5 version:

```bash
roslaunch mycobot_280 test.launch
```

Open rviz and get the following result:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz-5.png
width ="500" align = "center">

If you want to learn more about rviz, you can go to the [official document](http://wiki.ros.org/rviz) to view it

## M5 version prerequisites

- Open the console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>), open the terminal window to view the device name:

```bash
# View the device name of the robot
ls /dev/ttyUSB* # Old version myCobot280 M5

# If the terminal does not display the /dev/ttyUSB related name, you need to use the following command
ls /dev/ttyACM* # New version myCobot280 M5
```

- Grant serial port permissions to the robot:

```bash
# The default device name is /dev/ttyUSB0. If the device name is not the default value, it needs to be modified.
sudo chmod 777 /dev/ttyUSB0 # Old version myCobot280 M5

sudo chmod 777 /dev/ttyACM0 # New version myCobot280 M5
```

Then enter the user password (**Note:** The password will not be displayed, just enter it correctly).

# 280 series rviz user guide

## Robot arm control

>>**Note:** For better motion effects, the Atom firmware version of the end arm is 6.5, and the python driver library pymycobot version is 3.5.3

### Slider control

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 slider_control.launch port:=/dev/ttyUSB0 baud:=115200
```
It will **open rviz and a slider component**, you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/caf-1.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider**. If you want the real mycobot to move with you, you need to open another command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**Please note: due to the commandThe robot arm will move to the current position of the model while inputting. Before you use the command, please make sure that the model in rviz does not have any penetration**
**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**

### Model following

In addition to the above controls, we can also **let the model follow the real robot arm movement**. Open a command line and run:
- mycobot 280-M5 version:
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 follow_display.py _port:=/dev/ttyUSB0 _baud:=115200
```

Then open another command line and run:
- mycobot 280-M5 version:
```bash
roslaunch mycobot_280 mycobot_follow.launch
```
It will **open rviz to show the model following effect**.

### GUI control

Based on the previous, this package also **provides a simple Gui control interface**. This method is intended for real robotic arms to interact with each other, please connect mycobot.

Open the command line:
- mycobot 280-M5 version:
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 simple_gui.launch port:=/dev/ttyUSB0 baud:=115200
```
<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/gui-1.png
width ="500" align = "center">

### Keyboard control

**Added the keyboard control function** in the `mycobot_280` package, and synchronized it in real time in rviz. This function depends on pythonApi, so make sure it is connected to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard.launch port:=/dev/ttyUSB0 baud:=115200
```

The running effect is as follows:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/kb-1.png
width ="500" align = "center">

The command line will output mycobot information as follows:
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

Next, open another command line and run:

- mycobot 280-M5 version:

```bash
rosrun mycobot_280 teleop_keyboard.py
#or
rosrun mycobot_280 teleop_keyboard.py _speed:=70
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

currently: speed: 50 change percent 5
```

In this terminal, you can control the state of the robot and move the robot through the keys in the command line.

Parameters supported by this script:

+ _speed: robot movement speed.

+ _change_percent: movement distance percentage.

### Vision

>Install the camera at the end of mycobot. This vision part uses the eye-in-hand method. After reinstalling the camera, a hand-eye calibration is required.

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/camera_connect-1.jpg
width ="500"  align = "center">

#### Prerequisites for use

##### Python dependency libraries

Use pip to install the following Python libraries

```bash
pip install stag-python

pip install opencv-python

pip install scipy

pip install numpy

pip install pymycobot
```

##### Stag Code

This article uses stag code for QR code tracking. It is recommended to use color printing, as the recognition rate of black and white printing is low.

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/stag.png
width ="500"  align = "center">

Download address: [Stag code download](https://drive.google.com/drive/folders/0ByNTNYCAhWbILXd2SE5FY1c3WXM?resourcekey=0-nWeENtNZql2j9AF32Ud8sQ)

**Note**: The upper left corner of the stag code is a number, which can be identified by the stag recognition library of OpenCV. You can design different behavior logic for different numbers, such as 00 is set for position tracking, 01 is set for posture tracking, and 02 is set for returning to the observation point.

##### Firmware Update

Using the stag tracking firmware will give better results. This firmware will limit the deflection of the robot arm. Using the send_coords interface in refresh mode will filter out adjacent coordinates with an angle deviation of more than 90°.

The firmware is named `mycobot280_atom0926_vision.bin` and is located in the folder `~/mycobot_ros/mycobot_280/mycobot_280/config` of this project.

##### Camera initialization

In this project, the file `~/mycobot_ros/mycobot_280/mycobot_280/camera_calibration/camera_calibration.py` defines a visual recognition class called camera_detect.

```bash
class camera_detect:
    #Camera parameter initialize
    def __init__(self, camera_id, marker_size, mtx, dist):
```

The four parameters initialized are:

```bash
camera_id 相机编号（范围一般是0~10，默认为0）
marker_size Stag码的边长（mm）
mtx, dist 相机参数
```

An initialization example has been given in the program. The user only needs to modify camera_id and marker_size.

```bash
camera_params = np.load("camera_params.npz")  # Camera Profiles
mtx, dist = camera_params["mtx"], camera_params["dist"]
m = camera_detect(0, 32, mtx, dist)
```

**Note**: The default camera_id in Linux system is usually 0. If it is wrong, change it to other parameters from 0 to 10.

#### Hand-eye calibration

##### Hand-eye matrix principle

Hand-eye calibration is an essential part of visual tracking. Its function is to obtain the relative relationship between the robot arm coordinate system (hand) and the camera coordinate system (eye). We use a 4*4 hand-eye matrix to represent this relative relationship. The specific principle can be referred to: [Hand-Eye Matrix Principle](https://blog.csdn.net/weixin_45844515/article/details/125571550)

##### Hand-eye calibration method

> **Note:** After reinstalling the camera, a hand-eye calibration is required.

Install the camera on the robotic arm (usually at the end of the robotic arm) and connect the robotic arm to be controlled.

Run the command line:

- mycobot 280-M5版本：
  
```python
cd ~/mycobot_ros/mycobot_280/mycobot_280/camera_calibration  # The terminal switches to the target path
python3 camera_calibration.py  # Camera id, default is 0.
```

At this time, the robotic arm will first move to the observation posture.

```python
self.origin_mycbot_level = [0, 5, -104, 14, 0, 0]
def Eyes_in_hand_calibration(self, ml):
    ml.send_angles(self.origin_mycbot_level, 50)  # 移动到观测点
```

**Note**: Users can customize the observation points, such as rotating the 6 joints to put the camera in a more suitable position.

1. After moving to the observation posture, the terminal will pop up the following prompt, place the stag code in the camera's field of view, and enter any key to continue recognition.

```bash
make sure camera can observe the stag, enter any key quit
```

2. If the camera recognizes the stag code, it will automatically enter the next step of recognition, the robot arm moves and captures the position information of the robot arm and camera.

```bash
Move the end of the robot arm to the calibration point, press any key to release servo
```

3. After attaching, follow the prompts and enter any key to complete the hand-eye calibration.

```bash
focus servo and get current coords
```

4. The EyesInHand_matrix information will be printed at this time, and the calibration is considered complete. The "EyesInHand_matrix.json configuration file is generated. After the calibration is successful, there is no need to repeat the operation!

Please refer to the following video for specific effects, the effect is similar to mycobot 280:

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/mycobot_hand_vision.mp4" type='video/mp4' >
</video>

**Note**: **Hand-eye calibration may have errors due to improper operation, machine virtual position, etc. When the visual tracking effect is not good, hand-eye calibration needs to be re-performed**

#### Visual Tracking

>> The control method of the robot arm in this case: Use the topic in ROS for communication.
USB camera startup method: Use the camera usb_cam node in ROS to start.

usb_cam installation command:

```bash
# Ubuntu 20.04 
sudo apt install ros-noetic-usb-cam   
```

Mainly involved code files:

[1. communication_topic.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_communication/launch/communication_topic.launch)

[2. mycobot_topics.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_communication/scripts/mycobot_topics.py)

[3. open_camera.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/launch/open_camera.launch)

[4. listen_real_of_topic.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/scripts/listen_real_of_topic.py)

[5. detect_marker_with_topic.launch](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/launch/detect_marker_with_topic.launch)

[6. detect_stag.py](https://github.com/elephantrobotics/mycobot_ros/blob/noetic/mycobot_280/mycobot_280/scripts/detect_stag.py)

The default camera device parameter in the camera file `open_camera.launch` is `/dev/video0`.

```bash
<!-- //Specify the device file name, the default is /dev/video0 -->
    <param name="video_device" value="/dev/video0" />
```

Command line operation:

- mycobot 280-M5 version:
  
```bash
cd ~/catkin_ws
source devel/setup.bash
# The default serial port name of mycobot 280-M5 is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 detect_marker_with_topic.launch port:=/dev/ttyUSB0 baud:=115200
```

+ port: serial port string
+ baud: baud rate

The status of mycobot will be displayed in real time.

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/vision-5.png
width ="500"  align = "center">

Then run the stag recognition and tracking script. Open a new command line:

- mycobot 280-M5 version:

```bash
cd ~/catkin_ws
source devel/setup.bash
rosrun mycobot_280 detect_stag.py
```

After starting, the robot arm will move to the observation point:

```bash
self.origin_mycbot_horizontal = [0,60,-60,0,0,0]
ml.send_angles(self.origin_mycbot_horizontal, 50)  # 移动到观测点
```

The specific effects are as follows:

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/280_vision.mp4" type='video/mp4' >
</video>

### End effector

- **Supported end effectors:** myCobot Adaptive Gripper, myCobot Vertical Suction Pump V2.0, Camera Flange

- **Applicable devices:** myCobot 280 M5, myCobot 280 PI

> Note: myCobot Adaptive Gripper only supports myCobot 280 M5 devices

#### myCobot Adaptive Gripper

##### 1 Load the model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_gripper.launch
```

It will **open rviz**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-10.png
width ="500" align = "center">

##### 2 Slider Control

Open a command line and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, the serial port name can be changed to "/dev/ttyACM0".
roslaunch mycobot_280 slider_control_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-11.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider. ** If you want the real myCobot to move with you, you need to ** open another command line ** and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 slider_control_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```
**Please note: Since the robot arm will move to the current position of the model while the command is input, please make sure that the model in rviz does not have a model penetration phenomenon before you use the command**.
** Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**.

##### 3 Model following

In addition to the above control, we can also ** let the model follow the movement of the real robot arm**. Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 follow_display_gripper.py _port:=/dev/ttyUSB0 _baud:=115200
```

Then open another command line and run:

- mycobot 280-M5 version:

```bash
roslaunch mycobot_280 mycobot_follow_gripper.launch
```

It will **open rviz to show the model following effect**.

##### 4 GUI control

Based on the previous, this package also provides a simple Gui control interface. This method is intended to allow real robotic arms to interact with each other. Please connect myCobot.

Open the command line:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 simple_gui_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a GUI interface**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-12.png
width ="500" align = "center">

##### 5 Keyboard control

**Keyboard control function has been added to the `mycobot_280` package**, and it is synchronized in real time in rviz. This function relies on pythonApi, so make sure it is connected to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_gripper.launch port:=/dev/ttyUSB0 baud:=115200
```

The running effect is as follows:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-10.png
width ="500" align = "center">

The command line will output mycobot information, as follows: 
```SUMMARY
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

Pump control:
b - open
m - close

Other:
1 - Go to init pose
2 - Go to home pose
3 - Resave home pose
q - Quit

currently: speed: 50 change percent 5
```

In this terminal, you can control the state of the robot and move the robot by pressing keys in the command line.

Parameters supported by this script:

+ _speed: robot movement speed.
+ _change_percent: percentage of moving distance.

#### myCobot vertical pump V2.0

##### 1 Load the model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_pump.launch
```

It will **open rviz** and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-13.png
width ="500" align = "center">

##### 2 Slider control

> **Note: This function only supports the control of the robot**

Open a command line and run:

- myCobot 280-M5 version:

```bash
### The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 slider_control_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-16.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider. ** If you want the real myCobot to move with you, you need to **open another command line** and run:

- myCobot 280-M5 version:

```bash
### The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**Please note: Since the robot will move to the current position of the model when the command is input, please make sure that the model in rviz does not have any penetration before you use the command**.
**Do not drag the slider quickly after connecting the robot to prevent damage to the robot**.

##### 3 GUI control

Based on the previous, this package also **provides a simple Gui control interface**. This method is intended for real robots to interact with each other, please connect myCobot.

Open the command line:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 simple_gui_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a GUI interface**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-14.png
width ="500" align = "center">

##### 4 Keyboard control

**Added keyboard control function** in the `mycobot_280` package, and synchronized in real time in rviz. This function depends on python API, so make sure to connect to the real robot arm.

Open a command line and run:

- mycobot 280-M5 version:

```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 teleop_keyboard_pump.launch port:=/dev/ttyUSB0 baud:=115200
```

The running effect is as follows:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-13.png
width ="500" align = "center">

Next, open another command line and run:

- mycobot 280-M5 version:

```bash
rosrun mycobot_280 teleop_keyboard.py
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

Pump control:
b - open
m - close

Other:
1 - Go to init pose
2 - Go to home pose
3 - Resave home pose
q - Quit

currently: speed: 50 change percent 5
```

In this terminal, you can control the state of the robot and move the robot through the keys in the command line.

Parameters supported by this script:

+ _speed: robot movement speed.

+ _change_percent: movement distance percentage.

#### Camera Flange

##### 1 Load the model

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

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-15.png
width ="500" align = "center">

##### 2 Slider Control

> **Note: This function only supports the control of the robot**

Open a command line and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
roslaunch mycobot_280 slider_control_camera_flange.launch port:=/dev/ttyUSB0 baud:=115200
```

It will **open rviz and a slider component**, and you will see the following screen:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-17.png
width ="500" align = "center">

Then you can **control the movement of the model in rviz by dragging the slider. ** If you want the real myCobot to move with you, you need to **open another command line** and run:

- myCobot 280-M5 version:

```bash
# The default serial port name of myCobot 280-M5 version is "/dev/ttyUSB0" and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280 slider_control.py _port:=/dev/ttyUSB0 _baud:=115200
```

**Please note: Since the robot will move to the current position of the model when the command is input, please make sure that the model in rviz does not have any penetration before you use the command**.
**Do not drag the slider quickly after connecting the robot to prevent damage to the robot**.

#### Camera Flange && Pump

##### 1 Load the model

Open a command line and run:

- myCobot 280-M5 version:

```bash
roslaunch mycobot_280 test_camera_flange_pump.launch
```

It will **open rviz** and you will see the following:

<img src =../../../../../resources\3-FunctionsAndApplications\6.developmentGuide\ROS\ROS1\rviz/rviz280/12.1.4-18.png
width ="500" align = "center">

#### URDF model address

##### 1 myCobot adaptive gripper

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_gripper_parallel.urdf)

##### 2 myCobot vertical suction pump V2.0

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_pump.urdf)

##### 3 Camera flange

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange.urdf)

##### 4 Camera flange && suction pump

- [myCobot 280-M5 version](https://github.com/elephantrobotics/mycobot_ros/tree/noetic/mycobot_description/urdf/mycobot/mycobot_with_camera_flange_pump.urdf)