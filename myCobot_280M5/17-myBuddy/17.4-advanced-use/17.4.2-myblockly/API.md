
## 3. Building block API introduction

### 3.1 system information

#### 3.1.1 Get the Robot version


**1. Runtime API Reference**

- **Function:**Get robot version information
- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** : Robot version information


**2. Block display**  

<img src="../../../resourse/17-myBuddy/blockly/getrobotversion.png" style="zoom: 50%;" />	



#### 3.1.2 Checking the Software Version



**1. Runtime API Reference**

- **Function:**get software version
- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：version information

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getsysversion.png" style="zoom:50%;" />	

#### 3.1.3 Get Robot ID

**1. Runtime API Reference**

- **Function:**Get Robot ID
- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：ID

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getrobotid.png" style="zoom:50%;" />	



#### 3.1.4 Set Robot ID

**1. Runtime API Reference**

- **Function:**Set Robot ID
- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
  + `NUM` ：integer（1~253）
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/setrid.png" style="zoom:50%;" />	



### 3.2 The overall state of the manipulator


#### 3.2.1 Power on

**1. Runtime API Reference**

- **Function:**Power on the manipulator

- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/poweron.png" style="zoom:50%;" />	

#### 3.2.2 Power iff

**1. Runtime API Reference**

- **Function:**Power off the manipulator


- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/poweroff.png" style="zoom:50%;" />	



#### 3.2.3 Check whether the mechanical arm is powered on



**1. Runtime API Reference**

- **Function:**Check whether the mechanical arm is powered on


- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：
  + 1 power on 
  + 0 power down
  + -1 error

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/rpoweroff.png" style="zoom:50%;" />	

#### 3.2.4 Release all servos

**1. Runtime API Reference**

- **Function:**Release all servos
- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/releaseallservos.png" style="zoom:50%;" />	

#### 3.2.5 check control connection


**1. Runtime API Reference**

- **Function:**Check whether the manipulator control is connected


- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：unknown

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/controlisconnected.png" style="zoom:50%;" />	

#### 3.2.6 Robot error detection



**1. Runtime API Reference**

- **Function:**Robot error detection

- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：none

**2. Block display**  

<img src="../../../resourse/17-myBuddy/blockly/errorcheck.png" style="zoom:50%;" />	

#### 3.2.7 Set instruction refresh mode



**1. Runtime API Reference**

- **Function:**Set instruction refresh mode


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `MODE` ： Interpolation mode, non-interpolation mode (default)

- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/setfreshmode.png" style="zoom:50%;" />	

#### 3.2.8 Free mode state



**1. Runtime API Reference**

- **Function:**Set the free mode state of the manipulator


- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
  + `STATUS` ：status(open/close)
- **Return*** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/setfreemode.png" style="zoom:50%;" />	

#### 3.2.9 Check whether it is in free mode



**1. Runtime API Reference**

- **Function:**Check whether the manipulator is in free mode


- **Arguments:**
  + `ID(ALL/L/R/W)` ： ALL for ALL manipulator arms, L for left arm, R for right arm, W for waist
- **Return** ：
  + 0 no
  + 1 yes

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/checkisfree.png" style="zoom:50%;" />	

### 3.3 MDI control

#### 3.3.1 Read single Angle



**1. Runtime API Reference**

- **Function:**Read single Angle


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id（1~6）
- **Return** ：single angle

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getangle.png" style="zoom:50%;" />	

#### 3.3.2 Read all angles

**1. Runtime API Reference**

- **Function:**Read all angles of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：
  + `ANGLES` ：List of joint angles corresponding to the manipulator (including the angles from joint 1 to joint 6)



**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getangles.png" style="zoom:50%;" />	

#### 3.3.3 Send single angle

**1. Runtime API Reference**

- **Function:**Set the single Angle of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT_ID` ：joint1~6
  + `ANGLE` ：angle
  + `SPEED` speed(0~100)
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/sendangle.png" style="zoom:50%;" />	

#### 3.3.4 Send all angles



**1. Runtime API Reference**

- **Function:**Set all the angles of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `ANGLES` : Angle from joint 1 to joint 6
  + `SPEED` ：Moving speed of mechanical arm (0~100)

- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/sendangles.png" style="zoom:50%;" />	

#### 3.3.5 Read single coordinate

**1. Runtime API Reference**

- **Function:**Read the coordinates of a single joint of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for the waist
  + `COORD` ：1~6（x/y/z/rx/ry/rz）
  + `SPEED` : speed(0~100)
- **Return** : single coordinate

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getangle.png" style="zoom:50%;" />	

#### 3.3.6 Read all coordinates

**1. Runtime API Reference**

- **Function:**Read all coordinates of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：
  + `COORDS` : All joint coordinates of the manipulator



**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/getangles.png" style="zoom:50%;" />	

#### 3.3.7 Send single coordinate

**1. Runtime API Reference**

- **Function:**Set a single coordinate of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `COORD` ：Coordinate ID, range 1~6（x/y/z/rx/ry/rz）
  + `DATA` ：coordinate data
  + `SPEED` : speed(0~100)
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/sendangle.png" style="zoom:50%;" />	

#### 3.3.8 Send all coordinates

**1. Runtime API Reference**

- **Function:**Set all coordinates of the manipulator
- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `COORDS` : Coordinates of joints 1 to 6
  + `SPEED` : The moving speed of the manipulator(0~100)
  + `MODE` ： 0 - moveJ, 1 - moveL, 2 - moveC
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/sendangles.png" style="zoom:50%;" />	

### 3.4 Motion control

#### 3.4.1 Pause

**1. Runtime API Reference**

- **Function:**Suspend the movement of the manipulator


- **Arguments:**
  + `ID(ALL/L/R/W)` : All for all arms , for the left arm, R for the right arm，W for waist
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/pause.png" style="zoom:50%;" />	

#### 3.4.2 Is paused

**1. Runtime API Reference**

- **Function:**Check whether the manipulator is suspended


- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all arms，L for the left arm, R for the right arm，W for waist
- **Return** ：
  + 1 paused
  + 0 did not pause
  + -1 error

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/ispaused.png" style="zoom:50%;" />	

#### 3.4.3 Resume

**1. Runtime API Reference**

- **Function:**Restore the movement of the manipulator


- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all arms，L for the left arm, R for the right arm，W for waist
- **Return** ：none

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/resume.png" style="zoom:50%;" />	

#### 3.4.5 Is moving

**1. Runtime API Reference**

- **Function:**Check if the arm is moving

- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all arms，L for the left arm, R for the right arm，W for waist
- **Return** ：
  + 1 moving
  + 0 did not move
  + -1 error

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/ismoving.png" style="zoom:50%;" />	

#### 3.4.6 Whether to reach the specified position



 **1. Runtime API Reference**

- **Function:**Check whether the manipulator reaches the specified position


- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all arms，L for the left arm, R for the right arm，W for waist
  + `DATA` : Data list: 13 data for ALL, 6 data for L/R, and 1 data for W

  + `MODE` : Mode (Angles/Coords)

- **Return** ：
  + 1 yes
  + 0 no
  + -1 error

**2. Block display** 

<img src="../../../resourse/17-myBuddy/blockly/isinposition.png" style="zoom:50%;" />	

#### 3.4.7 Angles list

 **1. Runtime API Reference**

- **Function:** for **3.4.6 Whether to reach the specified position** separately set the list, can be filled in 6 angles

- **Arguments:**

  + `DATA` ：Data list, fill in 6 angles
    

- **Return** ：

  + `ANGLES` : Angle list (length 6)



**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/joints.png" style="zoom:50%;" />	

#### 3.4.8 Coordinates list

 **1. Runtime API Reference**

- **Function:** for **3.4.6 Whether to reach the specified location** separately set the list, can be filled in 6 coordinates
- **Arguments:**

  + `DATA` : Data list, fill in 6 coordinates



​    

- **Return** ：

  + `COORDS` ：Coordinate list (length 6)

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/coords.png" style="zoom:50%;" />	

### 3.5 Jog control

#### 3.5.1 Jog angle

 **1. Runtime API Reference**

- **Function:**Jog angle
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id，1~6
  + `DIRECTION` ：0-decrease  1-increase
  + `SPEED` ：speed(0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jogangle.png" style="zoom:50%;" />	

#### 3.5.2 Jog absolute

**1. Runtime API Reference**

- **Function:**Jog absolute
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id，1~6
  + `AGNLE` ：angle
  + `SPEED` ：speed(0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jogabsolute.png" style="zoom:50%;" />	

#### 3.5.3 Jog coordinate

 **1. Runtime API Reference**

- **Function:**Jog coordinate
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `COORD` ：coordinate 1~6（x/y/z/rx/ry/rz)
  + `DIRECTION` ：0-decrease  1-increase
  + `SPEED` speed (0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jogcoord.png" style="zoom:50%;" />	

#### 3.5.4 Jog stop

 **1. Runtime API Reference**

- **Function:**Jog stop
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jogstop.png" style="zoom:50%;" />	

#### 3.5.5 Jog increment

 **1. Runtime API Reference**

- **Function:**Set jog increment
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id（1~6）
  + `INCREMENT` increment (integer)
  + `SPEED` speed (0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jogincrement.png" style="zoom:50%;" />	

### 3.6 Encoder

#### 3.6.1 Set encoder

 **1. Runtime API Reference**

- **Function:**Set the potentiometer code of the manipulator
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint 1~6
  + `ENCODER` :value (integer)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setencoder.png" style="zoom:50%;" />	

#### 3.6.2 Get encoder

 **1. Runtime API Reference**

- **Function:**Obtain the potentiometer code of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint 1~6
- **Return** ：
  + `ENCODER` : value(0 ~ 4096)

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getencoder.png" style="zoom:50%;" />	

#### 3.6.3 Get encoders

**1. Runtime API Reference**

- **Function:**Obtain all potentiometer codes of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：
  + `ENCODERS` : encoders list

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getencoders.png" style="zoom:50%;" />	

#### 3.6.4 Set encodes

**1. Runtime API Reference**

- **Function:**Obtain all potentiometer codes of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `ENCODERS` ：encodes list(lenth 6)
  + `SPEED` speed(0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setencoders.png" style="zoom:50%;" />	

### 3.7.1 Running status

#### 3.7.1 Get speed

**1. Runtime API Reference**

- **Function:**Get the speed of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  + `SPEED` speed(0~100)

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getspeed.png" style="zoom:50%;" />	

#### 3.7.2 Set speed

**1. Runtime API Reference**

- **Function:**Set the speed of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SPEED` ：speed(0~100)
- **Return** ：none

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setspeed.png" style="zoom:50%;" />	

### 3.8 Joint limit

#### 3.8.1 Read the minimum joint Angle


**1. Runtime API Reference**

- **Function:**Read the minimum joint Angle of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
- **Return** ：
  - `ANGLE` ：angle

 **2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getminjointangle.png" style="zoom:50%;" />	

#### 3.8.2 Read the maximum joint Angle



**1. Runtime API Reference**

- **Function:**Read the maximum joint Angle of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
- **Return** ：
  - `ANGLE` : angle

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getmaxjointangle.png" style="zoom:50%;" />	

#### 3.8.3 Set the maximum joint Angle



**1. Runtime API Reference**

- **Function:**Set the maximum joint Angle of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
  + `ANGLE` : angle
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setmaxjointangle.png" style="zoom:50%;" />	

#### 3.8.4 Set the minimum joint Angle



**1. Runtime API Reference**

- **Function:**Set the minimum joint Angle of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
  + `ANGLE` ：angle
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setminjointangle.png" style="zoom:50%;" />	

### 3.9 Servo settings

#### 3.9.1 Joint state

**1. Runtime API Reference**

- **Function:**Check whether the specified joint of the manipulator is connected


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SERVOID` ：servo id(1~6)
- **Return** ：
  + 0 disenable
  + 1 enable
  + -1 error

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/isservoenable.png" style="zoom:50%;" />	

#### 3.9.2 Status of all joint connections



**1. Runtime API Reference**

- **Function:**Check whether all joints of the manipulator are connected


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  + 0 disenable
  + 1 enable
  + -1 error

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/isallservoenable.png" style="zoom:50%;" />	

#### 3.9.3 Get servo data

**1. Runtime API Reference**

- **Function:**Get servo data of the manipulator
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SERVOID` ：servo id(1~6)
  + `DATA_ID` : address
- **Return** ：
  + 0 disenable
  + 1 enable
  + -1 error

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getservodata.png" style="zoom:50%;" />	

#### 3.9.4 Power on a single motor



**1. Runtime API Reference**

- **Function:**Power on a single motor of the manipulator


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SERVOID` ：servo id(1~6)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/focusservo.png" style="zoom:50%;" />	

#### 3.9.5 Power off a single motor



**1. Runtime API Reference**

- **Function:**Power off a single motor of the manipulator
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SERVOID` ：servo id(1~6)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/releaseservo.png" style="zoom:50%;" />	

#### 3.9.6 Single joint brake



**1. Runtime API Reference**

- **Function:**The manipulator brakes on a single joint


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/jointbrake.png" style="zoom:50%;" />	

#### 3.9.7 Set motor zero



**1. Runtime API Reference**

- **Function:**Set motor zero

- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `JOINT` ：joint id(1~6)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setservocalibration.png" style="zoom:50%;" />	

#### 3.9.8 Set servo data 

**1. Runtime API Reference**

- **Function:**Set servo data
- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `SERVO_ID` ：servo id(1~6)
  + `DATA` : data address
  + `VALUE` ：value
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setservodata.png" style="zoom:50%;" />	

### 3.10 Acceleration settings

#### 3.10.1 Get acceleration

**1. Runtime API Reference**

- **Function:**Read the acceleration of all movements


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  + `SPEED` ：speed

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getspeed.png" style="zoom:50%;" />	

#### 3.10.2 Set movement acceleration



**1. Runtime API Reference**

- **Function:**Set movement acceleration


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
  + `ACC` ：integer(1~100)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setspeed.png" style="zoom:50%;" />	

### 3.11 M5Stack-basic

#### 3.11.1 Get basic input

**1. Runtime API Reference**

- **Function:**Get basic input
- **Arguments:**
  + `PIN_NO` ：integer(0~20)
- **Return** ：unknown

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getbasicinput.png" style="zoom:50%;" />	

#### 3.11.2 Set basic mode

**1. Runtime API Reference**

- **Function:**Set the base input/output mode


- **Arguments:**
  + `PIN_NO` ：integer(1~5)
  + `PIN_MODE` ：input/output 
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setbasicmode.png" style="zoom:50%;" />	

#### 3.11.3 Set basic output

**1. Runtime API Reference**

- **Function:**Set basic output
- **Arguments:**
  + `PIN_NO` ：integer(0~20)
  + `PIN_SIGNAL` ：low/high 
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setbasicoutput.png" style="zoom:50%;" />	

### 3.12 Atom

#### 3.12.1 Get digital input

**1. Runtime API Reference**

- **Function:**Get digital input
- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `PIN_NO` ：integer(1~5)
- **Return** : singal value

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getinput.png" style="zoom:50%;" />	

#### 3.12.2 Set color

**1. Runtime API Reference**

- **Function:**Set the color of the arm at the top of the robot arm


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `RED` ：integer(0~255)
  + `GREEN` : integer(0~255)
  + `BLUE` : integer(0~255)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setcolor.png" style="zoom:50%;" />	

#### 3.12.3 Set digital output

**1. Runtime API Reference**

- **Function:**Set digital output
- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `PIN_NO` ：integer(1~5)
  + `SIGNAL` ：0/1
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setdigitaloutput.png" style="zoom:50%;"/>	

#### 3.12.4 Set PinMode 

**1. Runtime API Reference**

- **Function:**Sets the state mode of the specified pin in the atom.


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `PIN_NO` ：integer(1~5)
  + `PIN_MODE` ：0 - input ，1-output
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setpinmode.png" style="zoom:50%;" />	

#### 3.12.5 Set PWM output

**1. Runtime API Reference**

- **Function:**Set PWM output
- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `CHANNEL` ：integer(1~5)
  + `FREQUENCY` ：frequency 0 - 1Mhz ，1- 10Mhz
  + `PIN_VAL` ：integer(0~100)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setpwmoutput.png" style="zoom:50%;" />	

### 3.13 Coordinates 

#### 3.13.1 Get end coordinates system

**1. Runtime API Reference**

- **Function:**Get end coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
- **Return** ：
  + 0 - flange，1 - tool

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getendtype.png" style="zoom:50%;" />	

#### 3.13.2 Set end coordinates system

**1. Runtime API Reference**

- **Function:**Set end coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `END` ：0 - flange ，1 - tool
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setendtype.png" style="zoom:50%;" />	

#### 3.13.3 Get movement type

**1. Runtime API Reference**

- **Function:**Get movement type
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
- **Return** ：
  + 1 - movel ， 0 - moveJ

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getmovementtype.png" style="zoom:50%;" />	

#### 3.13.4 Set movement type

**1. Runtime API Reference**

- **Function:**Set movement type
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `TYPE` ：1 - movel ， 0 - moveJ
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setmovetype.png" style="zoom:50%;" />	

#### 3.13.5 Get basic coordinates system

**1. Runtime API Reference**

- **Function:**Get basic coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
- **Return** ：
  - 0 - base ， 1 - tool

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getbasiccoord.png" style="zoom:50%;" />	

#### 3.13.6 Set basic coordinates system

**1. Runtime API Reference**

- **Function:**Set basic coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `TYPE` ：0 - base ， 1 - tool
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setbasiccoord.png" style="zoom:50%;" />	

#### 3.13.7 Get tool coordinates system

**1. Runtime API Reference**

- **Function:**Get tool coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
- **Return** ：
  - unknown

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/gettoolcoord.png" style="zoom:50%;" />	

#### 3.13.8 Set tool coordinates system

**1. Runtime API Reference**

- **Function:**Set tool coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `COORDS` ：coordinates list（lenth 6）
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/settoolcoord.png" style="zoom:50%;" />	

#### 3.13.9 Get world coordinates system

**1. Runtime API Reference**

- **Function:**Get world coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
- **Return** ：
  - unknown

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getworldcoord.png" style="zoom:50%;" />	

#### 3.13.10 Set world coordinates system

**1. Runtime API Reference**

- **Function:**Set world coordinates system
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `COORDS` ：coordinates list(length 6)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setworldcoord.png" style="zoom:50%;" />	

### 3.14 Gripper

#### 3.14.1 Get gripper angle

**1. Runtime API Reference**

- **Function:**Get gripper value
- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：
  - `GRIPPER_VALUE` ：gripper value

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getgrippercoord.png" style="zoom:50%;" />	

#### 3.14.2 Check that the gripper is in motion



**1. Runtime API Reference**

- **Function:**Check whether the gripper of the mechanical arm is moving


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：
  - `VALUE` ：0 - did not move，1-moving , -1 error

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/isgrippermoving.png" style="zoom:50%;" />	

#### 3.14.3 Set end claw zero


**1. Runtime API Reference**

- **Function:**Set the claw zero of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setgrippercalibration.png" style="zoom:50%;" />	

#### 3.14.4 Set the terminal claw state



**1. Runtime API Reference**

- **Function:**Set the terminal claw state


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `STATUS` ：0 - close 1 - open
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setgripperstatus.png" style="zoom:50%;" />	

#### 3.14.5 Set the claw range



**1. Runtime API Reference**

- **Function:**Set the claw value of the manipulator


- **Arguments:**
  + `ID(L/R)` ：L for the left arm, R for the right arm
  + `VALUE` ：integer(0~100)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setgrippervalue.png" style="zoom:50%;" />	

### 3.15 Collision detection 

#### 3.15.1 Get collision current



**1. Runtime API Reference**

- **Function:**Get collision current
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `JOINT_ID` ：joint id(1~6)
- **Return** ：
  - `CURRENT` ：current

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getjointcurrent.png" style="zoom:50%;" />	

#### 3.15.2 Set joint collision

**1. Runtime API Reference**

- **Function:**Set joint collision
- **Arguments:**
  + `ID(ALL/L/R)` ：ALL for all  arms，L for the left arm, R for the right arm
  + `JOINT_ID` ：joint id(1~6)
  + `CURRENT` ：integer
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setjointcurrent.png" style="zoom:50%;" />	

### 3.16 Plan speed

#### 3.16.1 Get planned acceleration



**1. Runtime API Reference**

- **Function:**Get planned acceleration


- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all  arms，L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `PLAN_ACCELERATION` ：planned acceleration list

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getplanacceleration.png" style="zoom:50%;" />	

#### 3.16.2 Get planned speed

**1. Runtime API Reference**

- **Function:**Get planned speed
- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all  arms，L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `PLAN_ACCELERATION` ：planned speed list

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getplanspeed.png" style="zoom:50%;" />	

#### 3.16.3 Set planned acceleration



**1. Runtime API Reference**

- **Function:**Set planned acceleration


- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all  arms，L for the left arm, R for the right arm，W for waist
  + `ACCELERATION` ：acceleration(0~100)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setplanacceleration.png" style="zoom:50%;" />	

#### 3.16.4 Set planned speed



**1. Runtime API Reference**

- **Function:**Set planned speed
- **Arguments:**
  + `ID(ALL/L/R/W)` ：ALL for all  arms，L for the left arm, R for the right arm，W for waist
  + `SPEED` ：planned speed(0~100)
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/setplanspeed.png" style="zoom:50%;" />	

### 3.17 Servo status

#### 3.17.1 Get joint current



**1. Runtime API Reference**

- **Function:**Get joint current


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `CURRENTS` ：joint currents

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getservocurrents.png" style="zoom:50%;" />	

#### 3.17.2 Get joint state



**1. Runtime API Reference**

- **Function:**Get joint state


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `LIST` ：List (voltage, sensor, temperature, current, Angle, overload, 0 indicates none error)


**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getservostatus.png" style="zoom:50%;" />	

#### 3.17.3 Acquisition of joint voltage



**1. Runtime API Reference**

- **Function:**Acquisition of joint voltage


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `VOLTS` ：voltage（less than 24V）

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getservovoltage.png" style="zoom:50%;" />	

#### 3.17.4 Get joint temperature



**1. Runtime API Reference**

- **Function:**Get joint temperature


- **Arguments:**
  + `ID(L/R/W)` ：L for the left arm, R for the right arm，W for waist
- **Return** ：
  - `TEMPERATURE` ：temperature

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/getservotemperature.png" style="zoom:50%;" />	



### 3.18 Execute in parallel

#### 3.18.1 Right arm workspace

**1. Runtime API Reference**

- **Function:**The mechanical arm is used synchronously. During the synchronous execution, the building blocks of the left and right arms need to be dragged to the working area to ensure the simultaneous movement of the two mechanical arms
- **Arguments:**none
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/rightarm.png" style="zoom:50%;" />	

#### 3.18.2 Left arm workspace

**1. Runtime API Reference**

- **Function:**The mechanical arm is used synchronously. During the synchronous execution, the building blocks of the left and right arms need to be dragged to the working area to ensure the simultaneous movement of the two mechanical arms
- **Arguments:**none
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/leftarm.png" style="zoom:50%;" />	

#### 3.18.3 Sync dot

**1. Runtime API Reference**

- **Function:**It can only be used in the working area of left and right arms, and only takes effect when running both arms synchronously. Using the synchronization point, the mechanical arm can stop and wait for the completion of the execution of the other mechanical arm under specified conditions before performing subsequent operations


- **Arguments:**none
- **Return** ：none

**2.Block display**

<img src="../../../resourse/17-myBuddy/blockly/syncdot.png" style="zoom:50%;" />	









