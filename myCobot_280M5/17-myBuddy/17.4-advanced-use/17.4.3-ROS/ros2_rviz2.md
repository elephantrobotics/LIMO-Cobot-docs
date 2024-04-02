# Control and following of the robot arm

## 1 Slider Control

Click the ROS2 Shell icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS2 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-17.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-18.jpg
 align = "center">
   <img src =../../../resourse/17-myBuddy/ROS/17.4.3-19.jpg
 align = "center">

Then run the command:

```bash
# The default serial port name of the mybuddy is "/dev/ttyACM0", and the baud rate is 115200".
ros2 launch mybuddy slider_control.launch.py
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src = ../../../resourse/17-myBuddy/ROS/17.4.3-4.jpg
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. The real mybuddy will move with it.


**Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm.**

### 2 Model Follow

In addition to the above controls, we can also make the model follow the movement of the real robotic arm . Open a ROS2 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-17.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-18.jpg
 align = "center">
    <img src =../../../resourse/17-myBuddy/ROS/17.4.3-19.jpg
 align = "center">

Then run the command:

```bash
# The default serial port name of the mybuddy is "/dev/ttyACM0", and the baud rate is 115200".
ros2 launch mybuddy mybuddy_follow.launch.py
```

It will open rviz to show the model following effect，the following picture：

<img src = ../../../resourse/17-myBuddy/ROS/17.4.3-5.jpg
width ="500"  align = "center">
