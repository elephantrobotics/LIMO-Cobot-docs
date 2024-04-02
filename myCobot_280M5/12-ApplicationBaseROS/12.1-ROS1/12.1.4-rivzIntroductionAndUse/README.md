# Brief introduction and use of rviz

rviz is a 3D visualization platform in ROS. On one hand, it can realize the graphical display of external information, and on the other hand, it can also release control information to an object through rviz, realizing the monitoring and control of a robot.

## 1 Installation of rviz and the introduction to its interface

When installing ros, if you perform a complete installation, rviz is already installed, and you may try to run it directly; if it is not fully installed, you may install rviz separately:

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

After the installation is complete, open a new terminal (shortcut key: <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the following command:
```bash
roscore
```

Then open a new terminal (shortcut key: <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and input the following command to open rviz.

```bash
rosrun rviz rviz
# or
rviz
```

Open rviz, and the following interface will be displayed:

<img src =../../../resourse/12-ApplicationBaseROS/rviz-1.png
width ="500"  align = "center">

### 1.1 Introduction of all areas

 * There is a list of monitors on the left. The monitor is a device that draws something in a 3D world and may have some options available in the display list.
 * On the top is a toolbar, which allows the user to use various function buttons to select tools with multiple functions.
 * The middle part is the 3D view: It is a main screen where various data can be viewed in three dimensions. The background color, fixed frame, grid, etc. of the 3D view can be set in detail in the Global Options and Grid items displayed on the left.
 * Below is the time display area, including system time and ROS time.
 * The right side is the observation angle setting area where different observation angles can be set.

We only give a rough introduction in this part. If you want to know more details, go to [User Guide](http://wiki.ros.org/rviz/UserGuide).

## 2 mycobot_ros installation and update

- **M5 Version:** Please refer to the end of the [13.1.1 Environment Building](../12.1.2-环境搭建.md) chapter.

- **PI版本(Ubuntu 20.04)：**

`mycobot_ros` is a ROS package from ElephantRobotics that works with all types of desktop robots.

The address of the project: https://github.com/elephantrobotics/mycobot_ros

The official default ROS1 workspace is `catkin_ws`.

Click the `ROS1 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then enter the following command:

```bash
cd ~/catkin_ws/src  # Enter the src folder of the workspace
# Clone the code on github
git clone https://github.com/elephantrobotics/mycobot_ros.git
cd ..       # return to the workspace
catkin_make # Build the code in the workspace
source devel/setup.bash # add environment variables
```

**Note:** If the `/home/er/catkin_ws/src(equivalent to ~/catkin_ws/src)` already exists in the `mycobot_ros` folder, you need to delete the `mycobot_ros` folder before running the above command. In the directory path, `er` is the user name of the VM. If they are different, change them.

## 3 Simple use

#### Start using launch file

This example is built on what you have already done [Environment building](../12.1.2-环境搭建.md) and you have successfully copied the company's code from GitHub to your virtual machine.

Open a new terminal (shortcut key: <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>)

Input the command to **configure the ROS environment**.

```bash
cd ~/catkin_ws/
source devel/setup.bash
```

Input again:

- mycobot 280-M5 version:

```bash
roslaunch mycobot_280 test.launch
```

- mycobot 280-Pi version:

```bash
roslaunch mycobot_280pi test.launch
```

- mycobot 280-JetsonNano version:
  
```bash
roslaunch mycobot_280jn test.launch
```



Open rviz, and then you will obtain the following result:

<img src =../../../resourse/12-ApplicationBaseROS/open-2.png
width ="500"  align = "center">

If you want to know more information about rviz, go to [Official documents](http://wiki.ros.org/rviz).

### 4 M5 Version Prerequisites

- Type Ctrl+Shift+T in the command terminal to open another terminal window in the same directory to view the device name:

```bash
# View the device name of the robotic arm
ls /dev/ttyUSB* # old version myCobot280 M5   

# If the terminal does not display the /dev/ttyUSB related name, you need to use the following command
ls /dev/ttyACM* # new version myCobot280 M5
```

- Grant the serial port permission to the robotic arm:

```bash
# The default device name is /dev/ttyUSB0, if the device name is not the default value, it needs to be modified.
sudo chmod 777 /dev/ttyUSB0 # old version myCobot280 M5 

sudo chmod 777 /dev/ttyACM0 # new version myCobot280 M5
```

Then enter the user password(**Note:** The password is not displayed, just enter it correctly).