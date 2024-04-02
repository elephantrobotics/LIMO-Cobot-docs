# 1 Windows Environment Build

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;First of all, it needs to be clear that all case experiments are implemented based on python+opencv+pymycobot, so when using the M5 robotic arm, you need to use Mystudio to burn ATOM firmware and M5Stack-basic firmware on the head and bottom of the robotic arm respectively.

- **Usage environment:** Windows 10 or Windows 11, Python3+OpenCV+pymycobot, Git
  
- **Applicable devices:** mypalletizer 260 M5


### **1.1 Install Python+pymycobot**

pymycobot is a Python package for serial communication with myCobot, supporting Python2, Python3.5 and later versions.

Before using pymycobot to control the robotic arm, you need to build a Python environment. For the specific building process, please refer to [Pyhton Environment Build](../../../7-ApplicationBasePython/7.1_download.md) 章节。

### **1.2 Install OpenCV**

OpenCV-Python is a Python-based library designed to solve computer vision problems. Before installation, make sure that the Python environment has been set up.

Open a console terminal (shortcut key Win+R, enter cmd to enter the terminal), enter the following command:

```bash
# The version numbers of the two need to be consistent, and version 4.6.0.66 is installed here
pip install opencv-python==4.6.0.66
pip install opencv-contrib-python==4.6.0.66
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装1.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装2.png
width ="500"  align = "center">

Install successfully, can check lib version and location with the command below

```bash
# to check python libs, format：pip show lib-name
pip show opencv-python
pip show opencv-contrib-python

# install pyqt5
pip install pyqy5
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装3.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装4.png
width ="500"  align = "center">

### **1.3 Install Git**

Git is an open source distributed version control system for effective and high-speed processing of project version management from small to very large.

* **Git official download address: https://gitforwindows.org/**

* **Click the `Download` option to start downloading Git**

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装1.png
width ="500"  align = "center">

* Double-click the downloaded exe file to install

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装2.png
width ="500"  align = "center">

* Select the installation location, the default is under the C drive, if you don’t want to put it under the C drive, you can change the location. After selecting the installation location, click next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装3.png
width ="500"  align = "center">

* By default, no icon will be created on the desktop, and a new feature has been added, adding GItBash to the Windows terminal, it is recommended to check it.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装4.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装5.png
width ="500"  align = "center">

* Choose a default editor, the default is Vim (Linux), and there is Notepad inside, I choose to use Vim

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装6.png
width ="500"  align = "center">

* The default name (master) after Git creates a branch. If there is no special default setting, click next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装7.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装8.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装9.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装10.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装11.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装12.png
width ="500"  align = "center">


* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装13.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装14.png
width ="500"  align = "center">

* The next step is the default, just select Next.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装15.png
width ="500"  align = "center">

* Additional configuration options are not selected by default, you can check these two boxes, support (node, python although there are still bugs) and then choose install.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装16.png
width ="500"  align = "center">

* After the installation is complete, click FInish to complete the installation.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装17.png
width ="500"  align = "center">

**checking**

Open a console terminal (shortcut key Win+R, enter cmd to enter the terminal), and enter the following command to view the Git version information:

```bash
git --version
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/git安装18.png
width ="500"  align = "center">

You need to use git to download the aikit_V2 package in the future. For the use of git, please refer to the link below:

* https://git-scm.com/book/zh/v2
* https://www.runoob.com/git/git-tutorial.html

### **1.4** aikit_V2 Install

`aikit_V2` is launched by ElephantRobotics, which is an artificial intelligence kit V2.0 package adapted to its desktop robotic arm.

project address: [https://github.com/elephantrobotics/aikit_V2](https://github.com/elephantrobotics/aikit_V2)


* 1 Double-click the `Git Bash` icon on the desktop to enter the Git terminal.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装1.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装2.png
width ="500"  align = "center">

* 2 Enter the following command in the Git terminal:

```bash
cd Desktop
git clone https://github.com/elephantrobotics/aikit_V2.git
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装3.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装4.png
width ="500"  align = "center">

Then the `aikit_V2` folder will appear on the desktop.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装5.png
width ="500"  align = "center">

At this point, the Windows environment is built.

# 2 Raspberry Pi Environment Construction

Since the Raspberry Pi version has a built-in Ubuntu 20.04 system, there is no need to build an environment.

- **Applicable devices:** myCobot 280 Pi、mechArm 270 Pi、myArm 300 Pi

### **2.1** Install OpenCV

Open a console terminal (shortcut key Ctrl+Alt+T), enter the command:

```bash
# The version numbers of the two need to be consistent, and version 4.6.0.66 is installed here
pip install opencv-python==4.6.0.66
pip install opencv-contrib-python==4.6.0.66
```

### **2.2** aikit_V2 Install

`aikit_V2` is launched by ElephantRobotics, which is an artificial intelligence kit V2.0 package adapted to its desktop robotic arm.

Applicable devices: myCobot 280 Pi、mechArm 270 Pi、myArm 300 Pi

project address: [https://github.com/elephantrobotics/aikit_V2](https://github.com/elephantrobotics/aikit_V2)


* 1 Open a console terminal (shortcut key Ctrl+Alt+T), enter the command:

```bash
git clone https://github.com/elephantrobotics/aikit_V2.git
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/树莓派安装1.png
width ="500"  align = "center">

* 2 Then under the main directory `/home/er`, there will be a folder named `aikit_V2`.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/树莓派安装2.png
width ="500"  align = "center">

So far, aikit_V2 has completed the installation.


### **2.3** mycobot_ros Install and update

`mycobot_ros` is a ROS package launched by ElephantRobotics that is suitable for all types of desktop robotic arms. It also integrates the artificial intelligence suit V2.0 program package.

Applicable devices: myCobot 280 Pi

project address: [https://github.com/elephantrobotics/mycobot_ros](https://github.com/elephantrobotics/mycobot_ros)

Click the `ROS1 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-1.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-2.jpg
 align = "center">

Then enter the following command:

```bash
cd ~/catkin_ws/src  # Go to the src folder in the workspace
# Clone the code on github
git clone https://github.com/elephantrobotics/mycobot_ros.git
cd ..       # return to workspace
catkin_make # Build the code in the workspace
source devel/setup.bash # Add environment variables
```

**Note:** If the `mycobot_ros` folder already exists in the `/home/er/catkin_ws/src (equivalent to ~/catkin_ws/src)` directory, you need to delete the original `mycobot_ros` before executing above command.
