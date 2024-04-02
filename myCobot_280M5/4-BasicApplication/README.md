# Application of Basic Functions

## [**1 myStudio**](4.1-myStudio/README.md)

Before using the equipment, you have to **install the driver and update the firmware**.

### [1.1 Installing the driver](4.1-myStudio/4.1.1-myStudio_download_driverinstalled.md)

According to the operating system used by him, the user can click the button below to download the zip file of the corresponding **CP210X** or **CP34X** drivers. After decompressing the file, select and install the installation package corresponding to the operating system.

There are two kinds of driver chip versions: **CP210X** (suitable for CP2104 version)/**CP34X** (suitable for CH9102 version) driver zip files. If you are not sure of the USB chip used for your equipment, you can install two drivers at the same time. (During the installation of **CH9102_VCP_SER_MacOS**, an error may be reported; however, the
installation has been done, and the error can be ignored.)

For Mac OS, ensure correct settings of the system "Preferred settings -> Security and privacy ->General" before installation, and allow the user to get it from App Store or an approved developer.

-   Download the **Basic** serial port driver **CP210X** 

  **CP210X**

  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Windows.zip)
  - [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_MacOS.zip)
  - [ **Linux** ](https://download.elephantrobotics.com/software/drivers/CP210x_VCP_Linux.zip)

  **CP34X**
  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_SER_Windows.exe)
  - [ **MacOS** ](https://download.elephantrobotics.com/software/drivers/CH9102_VCP_MacOS.zip)


-   Download the **Atom** serial port driver for the end.

  - [ **Windows10** ](https://download.elephantrobotics.com/software/drivers/CDM21228_Setup.zip)

![P210X_install](../resourse/4-BasicApplication/4.1/4.1.1.2-CP210X_install.gif)

### [1.2 Updating equipment firmware](4.1-myStudio/4.1.2-myStudio_flash_firmwares.md)

Prior to development, the user is required to confirm whether his equipment firmware is the latest version so that he can use the equipment better during subsequent development.

The user can update the firmware through **myStudio**.

##  [2 Factory firmware introduction](4.2-firmwares_intro/README.md)

### [2.1 Drag teaching](4.2-firmwares_intro/4.2.1-moving/README.md)

Robot drag teaching is a process during which the operator can drag the joints of the robot directly to make them do ideal postures and then make records corresponding thereto. The cobot is a system that has this function earlier. This kind of teaching avoids various disadvantages of traditional teaching, so it is a prospective technology for robot
applications.

### [2.2 Robot arm calibration](4.2-firmwares_intro/4.2.2-calibration/README.md)

Calibrating the robot arm is the precondition for precise control of the robot arm, and setting joint zero and initializing the potential of the motor are basic jobs for subsequent advanced development.

### [2.3 Communication forwarding](4.2-firmwares_intro/4.2.3-transponder/README.md)

Communication timeliness is vital to the micro-controller robot arm. For such arm, we often send control instructions to **M5Stack-basic** at the bottom. Through communication forwarding, the end effector analyzes the instructions and then implements target actions. At present, micro-controller devices have three methods of communication: **serial port, Bluetooth, and WIFI**. The user may choose an applicable method of
communication for programming.

### [2.4 Connection detection](4.2-firmwares_intro/4.2.4-connection/README.md)

Link test is a detection function that uses the motor in the robot arm and the connection state of **Atom**. The function allows the user to remove equipment faults easily.

During the link test, the connection state of the equipment for the robot arm, including the **connection of the servo** and the **communication state of Atom** can be seen. In micro-controller devices, the versions of their current firmwares are shown on M5Stack-basic.

## [3 Use for the first time](4.3-quick_start.md)

After knowing the current function of the firmware, connect and fix the machine by following the steps in this chapter, and start applying the basic functions of the equipment.
