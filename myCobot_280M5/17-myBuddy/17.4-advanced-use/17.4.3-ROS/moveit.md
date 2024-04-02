# myBuddy Moveit

`mycobot_ros` has integrated the MoveIt section.

Click the ROS1 Shell icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-1.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-2.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-3.jpg
 align = "center">

Then run the command:

```bash
roslaunch mybuddy_moveit demo.launch
```

If you want a real robot arm to execute a plan synchronously, you need to open another ROS1 environment terminal:

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-1.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-2.jpg
 align = "center">
  <img src =../../../resourse/17-myBuddy/ROS/17.4.3-3.jpg
 align = "center">

Then run the command:

```bash
# The default serial port name of the mybuddy is "/dev/ttyACM0", and the baud rate is 115200".
rosrun mybuddy_moveit sync_plan.py _port:=/dev/ttyACM0 _baud:=115200
```

Moveit has four control groups, the operation effect is as follows:

1.**Left Arm Control Group**: plan the movement direction of **left arm** by dragging the trackball.

<img src =../../../resourse/17-myBuddy/ROS/17.4.3-6.jpg
width ="500"  align = "center">

2.**Right Arm Control Group**: plan the movement direction of **right arm** by dragging the trackball.

 <img src =../../../resourse/17-myBuddy/ROS/17.4.3-7.jpg
width ="500"  align = "center">

