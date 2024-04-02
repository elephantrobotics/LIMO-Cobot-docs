# 1 Windows Environment Build

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;First of all, it's important to clarify that all the experimental cases are implemented based on Python + OpenCV + pymycobot. Therefore, when using the M5 robotic arm, you need to burn the ATOM firmware and M5Stack-basic firmware respectively onto the robotic arm's head and base using Mystudio.

- **Environment Required：** Windows 10 or Windows 11、Python3.9+OpenCV+pymycobot、PyQt6、Git、Deeyea Camera、RealSense Camera
  
- **Applicable devices:** mechArm 270 M5、myCobot 280 M5

- **Notice:** RealSense camera requires USB3.2 Type-C data cable + computer device USB3.0 port

### **1.1 Install Python+pymycobot**

pymycobot is a Python package that communicates with myCobot through serial communication, supporting Python 2, Python 3.5, and later versions.

Before using pymycobot to control the robotic arm, you need to set up the Python environment. For specific installation instructions, please refer to the documentation or instructions provided at the following link: [Pyhton + PyCharm Environment build](../../../7-ApplicationBasePython/7.1_download.md) 章节。

>> Note: The Python version should be installed as 3.9.10.

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

After successful installation, you can use the following command to view the specific installed version and installation location:

```bash
# You can also view other python libraries format: pip show library name
pip show opencv-python
pip show opencv-contrib-python
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

# 2 Use of Obi medium light Deeyea camera

- **Prerequisites for usage:** Python version 3.9, numpy version 1.21.0 or higher, and opencv-python version 4.6.0.66.

### **2.1** Download and Install the Driver.

Download Link：https://vcp.developer.orbbec.com.cn/resourceCenter?defaultSelectedKeys=45

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_1.png
width ="500"  align = "center">

### **2.2** Download OpenNI2 Viewer

OrbbecViewer for OpenNI2 is a tool developed based on the Orbbec OpenNI2 SDK, designed to assist developers in quickly utilizing Orbbec's 3D sensor products. The Orbbec OpenNI2 extension API is built on OpenNI2 and implements specific features and functions of Orbbec 3D sensor products, including reading serial numbers, retrieving device types, camera parameters, controls, and more.

Download Link：https://vcp.developer.orbbec.com.cn/resourceCenter?defaultSelectedKeys=108

Tutorial for Use：https://developer.orbbec.com.cn/technical_library.html?id=36

OrbbecViewer for OpenNI2 Demo Platform：Windows x64

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_2.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_3.png
width ="500"  align = "center">

### **2.3** Deeyea Camera Parameter Adjustment

Open the Deeyea camera tool (OpenNI2 Viewer), adjust some parameters of the color picture, turn off the priority automatic exposure and automatic exposure modes, set the exposure control value to 78, and some computers set it to 156.

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_3-1.png
width ="500"  align = "center">

### **2.4** Download Orbbec SDK

Download Link：https://vcp.developer.orbbec.com.cn/resourceCenter?defaultSelectedKeys=55

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_4.png
width ="500"  align = "center">

### **2.5** Download OpenNI2 SDK

Download Link：https://vcp.developer.orbbec.com.cn/resourceCenter?defaultSelectedKeys=69

Tutorial for Use：https://developer.orbbec.com.cn/technical_library.html?id=29

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_5.png
width ="500"  align = "center">

# 3 RealSense camera usage

-**Prerequisites for use:** Python version is 3.9, numpy version 1.21.0 and above, opencv-python version is 4.6.0.66, USB3.2 Type-C data cable + computer equipment USB3.0 port

### **3.1** RealSense Visualization Tool

RelalSense Camera Visualizer Download Link：[Intel.RealSense.Viewer.exe](https://github.com/IntelRealSense/librealsense/releases/download/v2.54.1/Intel.RealSense.Viewer.exe)

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/realsense_1.png
width ="500"  align = "center">

### **3.2** RealSense Camera Parameter Adjustment

借助RealSense相机可视化工具，调整彩色画面的某些参数，将曝光控制的值设置为78，部分电脑可能是改为156

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/realsense_2.png
width ="500"  align = "center">

# 4 Install Aikit_3D_UI

`Aikit_3D_UI` is launched by ElephantRobotics, which is an artificial intelligence kit 3D package adapted to its desktop robotic arm.

project address：[https://github.com/elephantrobotics/Aikit_3D](https://github.com/elephantrobotics/Aikit_3D)


### **4.1** Double-click the `Git Bash` icon on the desktop to enter the Git terminal.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装1.png
width ="500"  align = "center">

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装2.png
width ="500"  align = "center">

### **4.2** Choose different commands according to the model and device

After switching to the desktop in the Git terminal, enter the following command:

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_V2安装3.png
width ="500"  align = "center">

- mechArm 270 M5

```bash
cd Desktop
# If you use the Obi medium-light Deeyea camera, execute this command
git clone https://github.com/elephantrobotics/AiKit_3D_UI.git
# If using RealSense camera, execute this command
git clone -b realsense_UI https://github.com/elephantrobotics/AiKit_3D_UI.git
```

- myCobot 280 M5

```bash
cd Desktop
# If you use the Obi medium-light Deeyea camera, execute this command
git clone -b Deeyea_280_M5 https://github.com/elephantrobotics/AiKit_3D_UI.git
# If using RealSense camera, execute this command
git clone -b Realsense_280_M5 https://github.com/elephantrobotics/AiKit_3D_UI.git
```

<!-- <img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_6.png
width ="500"  align = "center"> -->

Then the `AiKit_3D_UI` folder will appear on the desktop.

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_7.png
width ="500"  align = "center">

### **4.3** Open project file

Use PyCharm to open the AiKit_3D_UI project folder

### **4.4** Create Virtual Environment

#### 4.4.1 Created with PyCharm

To create a virtual environment for the AiKit_3D_UI project folder in PyCharm.

  - Open PyCharm and navigate to the folder containing the AiKit_3D_UI project.
  - Click on the "File" menu, then select "Settings."
  - In the Settings dialog, choose "Project: AiKit_3D_UI," and click on "Python Interpreter."
  - In the top-right corner of the Python Interpreter page, click on the dropdown menu and select "Show All..."
  - In the popup window, click the "+" button in the top-left corner and choose "Add."
  - In the "Add Python Interpreter" window, you can either create a new virtual environment or use an existing interpreter.

<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_8.png
width ="500"  align = "center">
<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_9.png
width ="500"  align = "center">
<img src =../../../resourse/13-AdvancedKit/AiKit_3D/搭建_10.png
width ="500"  align = "center">

#### 4.4.2 Use terminal commands

Created through terminal command, where `virtual_name` is the custom virtual environment name:

```bash
# Create 
python -m venv virtual_name

# Activate virtual environment and enter
cd virtual_name/Scripts
activate
```

### **4.5** Download related packages
  
* Under the `AiKit_3D_UI` folder, open the terminal (prerequisite: make sure the terminal has entered the virtual environment) and enter:
  
  ```bash
  pip install -r requirements.txt
  ```

* **Prerequisite:** The creation of the virtual environment has been completed, and the terminal has entered the virtual environment.

* **Note:** The `requirements.txt` file is located in the `~/Desktop/AiKit_3D_UI` folder.

At this point, the Windows environment is built.
