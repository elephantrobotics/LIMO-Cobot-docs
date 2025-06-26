# 280M5 remote control case

**Function description**: Use the game controller to control the robot to move coordinates and open and close the gripper

## 1 Gripper installation
Insert the Lego connector into the reserved socket of the gripper

<img src="./img/g0.jpg" width="60%" height="60%" alt="">

Align the gripper with the connector inserted into the socket at the end of the robot arm and insert it

<img src="./img/g1.jpg" width="60%" height="60%" alt="">

Connect the extension line to the gripper

<img src="./img/g2.jpg" width="60%" height="60%" alt="">

Insert the robot arm control interface

<img src="./img/g3.png" width="60%" height="60%" alt="">

<img src="./img/g4.jpg" width="60%" height="60%" alt="">

## 2 Gripper test
```python
from pymycobot import MyCobot280,utils
import time
arm=MyCobot280(utils.get_port_list()[0])
time.sleep(1.5)
    for i in range(2):
    arm.set_gripper_state(1,100)#Gripper clamped
    time.sleep(1)
    arm.set_gripper_state(0,100)#Gripper open
    time.sleep(1)

```

## 3 Handle function description
**Note**: The handle needs to be purchased separately, please consult the official customer service for details

<img src="./img/joy.jpg" width="60%" height="60%" alt="">

Plug the receiver of the handle into the computer

|Button|Function|
|---|---|
|Press the direction key↑|RY positive movement|
|Press the direction key↓|RY negative movement|
|Press the direction key←|RX positive movement|
|Press the direction key→|RX negative movement|
|Push the left joystick↑|X positive movement|
|Push the left joystick↓|X negative movement|
|Push the left joystick←|Y positive movement|
|Push the left joystick→|Y negative movement|
|Push the right joystick↑|Z positive movement|
|Push the right joystick↓|Z negative movement|
|Push the right joystick←|RZ positive movement|
|Push the right joystick→|RZ negative movement|
|Press the Y key|Gripper open|
|Press the A key|Gripper close|

**Note**: Some handle buttons are not used, so they will not have any effect on the robot arm

## 4 Installation of handle dependency library
Open the terminal and enter the following command to install the handle driver library
```bash
pip install pygame
```
## 5 Preparation
Before connecting to the 12V power supply, you can manually adjust the robot arm to the zero position shown in the figure below, and then enter the 12V power supply and communication data line. There should be no debris around the robot arm to avoid collision

<img src="./img/280.png" width="60%" height="60%" alt="">


Turn on the switch of the handle

<img src="./img/joy_on.png" width="60%" height="60%" alt="">

Note whether the MODE LED of the handle is on

<img src="./img/joy_led.png" width="60%" height="60%" alt="">

**Note**: The robot arm can only be controlled when the MODE LED is on. If the handle is not used for a long time, it will enter the standby state. You can press the START button on the handle to activate it.

<img src="./img/joy_start.png" width="60%" height="60%" alt="">

## 6 Example program
```python
import pygame
import sys
import time
from pymycobot import MyCobot280,utils
mc=MyCobot280(utils.get_port_list()[0])
time.sleep(1.5)
init_angles=[0, 0, -90, 0, 0, 0]
mc.sync_send_angles(init_angles,50)
pygame.init()
pygame.joystick.init()
button_pressed = False
hat_pressed=False
previous_state = [0,0,0,0,0,0] 

def joy_handler():
    global button_pressed
    global hat_pressed
    global previous_state
    if event.type == pygame.JOYAXISMOTION:
        axis = event.axis  
        value = round(event.value, 2)  
        if abs(value) > 0.1:  
            flag = True
            previous_state[axis] = value  
            if axis==0 and value==-1.00:
                mc.jog_coord(2,1,50)
            elif axis==0 and value==1.00:
                mc.jog_coord(2,0,50)
            if axis==1 and value==1.00:
                mc.jog_coord(1,0,50)
            elif axis==1 and value==-1.00:
                mc.jog_coord(1,1,50)
            if axis==2 and value==1.00:
                mc.jog_coord(6,1,50)
            elif axis==2 and value==-1.00:
                mc.jog_coord(6,0,50)                    
            if axis==3 and value==1.00:
                mc.jog_coord(3,0,50)
            elif axis==3 and value==-1.00:
                mc.jog_coord(3,1,50)
        else:
            if previous_state[axis] != 0:  
                mc.stop()
                previous_state[axis] = 0  

    if event.type == pygame.JOYBUTTONDOWN:
        if joystick.get_button(3)==1:
            mc.set_gripper_state(0,100)
        if joystick.get_button(0)==1:
            mc.set_gripper_state(1,100)
                    
    if event.type == pygame.JOYHATMOTION:
        hat_value = joystick.get_hat(0) 
        if hat_value ==(0,-1):
            mc.jog_coord(5,1,50)
        elif hat_value ==(0,1):
            mc.jog_coord(5,0,50)
        elif hat_value ==(-1,0):
            mc.jog_coord(4,0,50)
        elif hat_value ==(1,0):
            mc.jog_coord(4,1,50)
        if hat_value != (0, 0):
            hat_pressed = True
        else:
            if hat_pressed:  
                mc.stop()
                hat_pressed = False  

if pygame.joystick.get_count() > 0:
    joystick = pygame.joystick.Joystick(0) 
    joystick.init()
else:
    print("No handle detected")
    pygame.quit()
    sys.exit()
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False       
        joy_handler()
pygame.quit()
```

## 7 Effect display

<img src="./img/280.gif" width="60%" height="60%" alt="">