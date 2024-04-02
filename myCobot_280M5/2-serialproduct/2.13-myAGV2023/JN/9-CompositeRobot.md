# Compound Robot

myAGV now supports three robotic arms: myCobot 280 M5/Pi, myPalletizer 260 M5/Pi, and mechArm 270 M5/Pi. myAGV can control the robotic arm through the USB serial port or wirelessly to realize mobile grabbing, expand the working space, and complete more tasks.

## 1 Installation Notes

### 1.1 Install the robotic arm

First, you need to install the robotic arm to myAGV. You can use Lego keys or screws to install the robotic arm on the upper part of myAGV, and you can install it on the front or rear according to your needs.

![myAGV2023](../../../resourse/13-AdvancedKit/myAGV/复合机器人/myAGV2023.png)

### 1.2 Connect the arm

Use the DC power cable to connect to the power supply interface of the robot arm, and connect the other end to the power interface of the robot arm. The car can supply power to the robot arm (12V 5A).

![myAGV2023API](../../../resourse/13-AdvancedKit/myAGV/复合机器人/myAGV2023API.jpg)

Example: myCobot 280 Pi, other Pi robotic arms are the same.

1. Use a hex wrench to remove the four M4*8 hexagon screws

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/A1.png)API

2. Install the myCobot 280Pi robotic arm in the correct direction corresponding to the X axis, and screw on four m4*8 to fix the 280Pi.

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/A2.png)

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/A3.png)

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/A4.png)

## 2 myAGV and robotic arm communication control

### 2.1 M5 Version

#### 2.1.1 USB serial communication control

**Note：** only support myCobot 280 M5、myPalletizer 260 M5、mechArm 270 M5

This section uses the myPalletizer 260 M5 version as an example.

1、Connect the arm

When using the usb serial communication control, first use the type-c to usb cable to connect the car and the robot arm.

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/A5.jpg)

2、USB communication connection

Click on Transponder, then click on USB UART, and the robotic arm stays on the Atom: ok interface.![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/图4.jpg)

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/图5.jpg)

3、myAGV communication control

The car is turned on normally and connected to the display screen and keyboard and mouse. The above steps ensure that the connection is good, and then the car can be used to control the robotic arm.

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/图8.png)

If you encounter a permission error indicating lack of access to the serial port after running:

```
PermissionError:[Errno 13]Permission denied:"/dev/ttyACM0"
```
You can resolve it by adding a serial port rule:

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/图9.png)

Fill in the following content:

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/图10.png)

Then save the serial port rule, and reload the rules in the terminal and reboot:

```
sudo  udevadm control --reload

sudo reboot
```

Afterward, you should be able to control the robotic arm normally.

For more detailed myBlockly tutorial, see
[**6.1 myBlockly**](../../5-ProgramingApplication-myblockly-uiflow-mind/README.md)

#### 2.1.2 WIFI communication control

**Note：** only support myCobot 280 M5、myPalletizer 260 M5

1、 mobile network settings

**Step 1:** It is necessary to modify the wifi or mobile hotspot to be consistent with the robotic arm network:

* namely "MyCobotWiFi2.4G". Meanwhile, change the password of hotspot as "mycobot123".

* namely "MyPalWiFi2.4G". Meanwhile, change the password of hotspot as "mypal123".


2、WIFI connection

**Step 1:** Press WLAN Server, and "WIFI Connecting" appears, signaling that the robotic arm is connecting with WIFI.

<img src="../../../resourse/7-ApplicationBasePython/TCPIP/WLAN Server1.jpg" style="zoom: 25%;" />

<img src="../../../resourse/7-ApplicationBasePython/TCPIP/wificonnecting.jpg" style="zoom: 25%;" />

**Step 2:** If the screen shows WIFI Connected, IP and Port, it means that robotic arm is successfully connected with WIFI.

<img src="../../../resourse/7-ApplicationBasePython/TCPIP/wificonnected.jpg" style="zoom: 25%;" />


> > **Notice:** If it fails to connect, go back to press USB UART and then try the steps above again.
>
> >If you still can't connect to WIFI, please refer to Chapter 8：[**7 TCP/IP**](../../7-ApplicationBasePython/7.6_TCPIP.md/) - 1.3 WIFI can't connect to the solution.

3、myAGV communication control case

The car is turned on normally and connected to the display screen and keyboard and mouse. The above steps ensure that the connection is good, and then the car can be used to control the robotic arm.

* myCobot 280：

```python
from pymycobot import MyCobotSocket
# Use port 9000 by default
# Where "192.168.10.22" is the IP of the robot arm
mc = MyCobotSocket("192.168.10.22",9000)

#After the connections is normal, the robot arm can be controlled.
res = mc.get_angles()
print(res)
mc.send_angles([0,0,0,0,0,0],20)
...
```

* myPalletizer 260：

```python
from pymycobot import MyPalletizerSocket
# Use port 9000 by default
# Where "192.168.10.22" is the IP of the robot arm
mc = MyPalletizerSocket("192.168.10.22",9000)

#After the connections is normal, the robot arm can be controlled.
res = mc.get_angles()
print(res)
mc.send_angles([0,0,0,0],20)
...
```

### 2.2 Pi version

#### 2.2.1 WIFI communication control

**Note：** only support myCobot 280 Pi、myPalletizer 260 Pi、mechArm 270 Pi

1、Configure the robotic arm

**Step 1**	First, connect the robotic arm to the display screen and turn it on, click the WIFI icon to connect to WIFI, enter the WIFI password, click Connection, and connect successfully.

**Step 2**	Click the desktop pymycobot file, click the demo file, and copy the Server.py file to the desktop.

**Step 3**	Open command terminal

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/server2.jpg)


**Step 4**	Enter the following code to run the script:

```python
sudo python3 Server.py
```

**Step 5** The operation is successful as shown in the figure:

![开启小车launch终端](../../../resourse/13-AdvancedKit/myAGV/复合机器人/server3.jpg)


2、myAGV communication control case

The car is turned on normally and connected to the display screen and keyboard and mouse. The above steps ensure that the connection is good, and then the car can be used to control the robotic arm.

**Note: The robot arm needs to be on the same network segment as the car, that is, the same WIFI.**

* myCobot 280、mechArm 270：

```python
from pymycobot import MyCobotSocket
# Use port 9000 by default
# Where "192.168.10.22" is the IP of the robot arm
mc = MyCobotSocket("192.168.10.22",9000)
mc.connect()  

#After the connections is normal, the robot arm can be controlled.
res = mc.get_angles()
print(res)
mc.send_angles([0,0,0,0,0,0],20)
...
```

* myPalletizer 260：

```python
from pymycobot import MyPalletizerSocket
# Use port 9000 by default
# Where "192.168.10.22" is the IP of the robot arm
mc = MyPalletizerSocket("192.168.10.22",9000)
mc.connect()   

#After the connections is normal, the robot arm can be controlled.
res = mc.get_angles()
print(res)
mc.send_angles([0,0,0,0],20)
...
```

