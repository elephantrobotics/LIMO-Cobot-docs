# 基础功能应用

在开始使用机械臂设备前，您首先需要**安装驱动以及更新设备固件**。

驱动程序是让您的电脑与机械臂进行通信的重要软件，安装驱动程序可以确保设备正常工作、优化性能，并启用设备的各种功能。因此，通常在新设备接入计算机时，系统会提示安装驱动程序，这是为了保证设备能够被正确识别和使用。设备固件是一种嵌入在硬件设备中的特定软件，它负责控制设备的基本操作和功能。固件位于软件和硬件之间，扮演着控制硬件操作的角色。您需要更新最新的设备固件，才能更好的对mycobot机械臂进行开发。

![P210X_install](../../../resources/3-FunctionsAndApplications/5.1-Functionlnstruction/atom_PC.jpg)



### 安装驱动

用户可根据自己所使用的操作系统，点击下方按钮下载相应的 **CP210X** 或 **CP34X** 驱动程序压缩包，在解压压缩包后，选择对应操作系统位数的安装包进行安装。

目前存在两种驱动芯片版本， **CP210X** （适用于CP2104版本）/**CP34X** （适用于CH9102版本）驱动程序压缩包。若您不确定您的设备所使用的USB芯片，可同时安装两种驱动。（ **CH9102_VCP_SER_MacOS** 在安装过程中，可能出现报错，但实际上已经完成安装，忽略即可。）

对于 Mac OS，在安装之前确保系统 "偏好设置->安全性和隐私->通用" ，并允许从 App Store 和被认可的开发者。

- 下载底部 **M5Stack-basic** 串口驱动程序
  **CP210X**
  
  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Windows.zip)
  - [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_MacOS.zip)
  - [ **Linux** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Linux.zip)
  
  **CP34X**
  
  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_SER_Windows.exe)
  - [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_MacOS.zip)
  
- 下载末端 **Atom** 串口驱动程序 
  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CDM21228_Setup.zip)

请根据此图来完成驱动程序的安装
![P210X_install](../../../resources/3-FunctionsAndApplications/5.1-Functionlnstruction/CP210X_install.gif)

### 更新设备固件

用户可通过 **myStudio**进行设备固件的更新，在开发前，用户请确认自己所使用的设备固件是否为最新版的固件，以便于用户在后续开发中更好的使用该设备。下一小节，将会介绍**myStudio**，以及如何通过**myStudio**进行固件升级。

##  **出厂固件介绍**

###  [拖动示教](../5.3-FirmwareFunctionDescription/5.3.1-moving/5.3.1.1-micro_controller.md)

机器人拖动示教，就是操作员可以直接拖着机器人各关节，运动到理想的姿态，记录下来。协作机器人是较早具有该功能的系统。这种示教方式可以避免传统示教的各种缺点，是机器人中一项很有应用前景的技术。

###  [校准机械臂](../5.3-FirmwareFunctionDescription/5.3.2-calibration/5.3.2.1-micro_controller.md)

校准机械臂是对机械臂精准控制的前提，设置关节零位，初始化电机的电位值是后续进行进阶开发的基础。

###  [通讯转发](../5.3-FirmwareFunctionDescription/5.3.3-transponder/5.3.3.1-micro_controller.md)

通讯的时效性对于微控制器机械臂至关重要，对于微控制器机械臂来说，我们通常对底部的 **Basic** 发送控制指令，通过通讯转发，末端执行器将对指令进行解析，继而执行目标动作。目前 **微控制类设备** 的通讯方式有：**串口通讯**、**蓝牙通讯**、**WIFI通讯**。用户可选择适用的通讯方式，进行编程操作。

###  [连接检测](../5.3-FirmwareFunctionDescription/5.3.4-connection/5.3.4.1-micro_controller.md)

连接检测是一项用机械臂中电机以及 **Atom** 连接状态的检测功能。这项功能便于客户排除设备故障。

连接检测中看到机械臂的设备连接状态，包括 **舵机的连接** 以及 **Atom 的通讯状态**。**微控制器类设备** 中  Basic 上会显示设备的当前固件版本。

