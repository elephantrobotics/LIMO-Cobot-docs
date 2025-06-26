# Basic Function Application

## **myStudio**
Before you start using the device, you first need to **install the driver and update the device firmware**.

### Install the driver

Users can click the button below to download the corresponding **CP210X** or **CP34X** driver package according to the operating system they are using. After unzipping the package, select the installation package corresponding to the operating system bit number for installation.

There are currently two driver chip versions, **CP210X** (for CP2104 version)/**CP34X** (for CH9102 version) driver package. If you are not sure about the USB chip used by your device, you can install both drivers at the same time. ( **CH9102_VCP_SER_MacOS** may have an error during the installation process, but it has actually been installed, so just ignore it.)

For Mac OS, make sure the system "Preferences->Security and Privacy->General" is set before installation, and allow downloads from the App Store and approved developers.

- Download the bottom **M5Stack-basic** serial port driver
**CP210X**

- [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Windows.zip)
- [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_MacOS.zip)
- [ **Linux** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Linux.zip)

**CP34X**
- [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_SER_Windows.exe)
- [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_MacOS.zip)

- Download the terminal **Atom** serial port driver
- [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CDM21228_Setup.zip)

Please follow this picture to complete the driver installation
![P210X_install](../../../resources/3-FunctionsAndApplications/5.1-Functionlnstruction/CP210X_install.gif)

###  Update device firmware

Before development, users should confirm whether the device firmware they are using is the latest version of the firmware, so that users can better use the device in subsequent development.

Users can update the device firmware through **myStudio**.

## **Factory firmware introduction**

### Drag teaching

Robot drag teaching means that the operator can directly drag the robot joints to move to the ideal posture and record it. Collaborative robots are the earliest systems with this function. This teaching method can avoid the various shortcomings of traditional teaching and is a technology with great application prospects in robots.

### Calibrating the robot arm

Calibrating the robot arm is the prerequisite for precise control of the robot arm. Setting the joint zero position and initializing the potential value of the motor are the basis for subsequent advanced development.

### Communication 

The timeliness of communication is crucial for microcontroller manipulators. For microcontroller manipulators, we usually send control instructions to the **Basic** at the bottom. Through communication forwarding, the end effector will parse the instructions and then execute the target action. Currently, the communication methods of **microcontroller devices** are: **serial communication**, **Bluetooth communication**, **WIFI communication**. Users can choose the applicable communication method and perform programming operations.

### Connection detection

Connection detection is a detection function for the connection status of the motor and **Atom** in the manipulator. This function is convenient for customers to troubleshoot equipment failures.

In the connection detection, the device connection status of the manipulator can be seen, including **servo connection** and **Atom communication status**. **Microcontroller devices** The current firmware version of the device will be displayed on Basic.

### First use

After understanding the existing functions of the firmware, please follow the steps in this section to start connecting and fixing the machine and start using the basic functions of the device.