# myArm-300 Moveit

`mycobot_ros` has now integrated the MoveIt part.

Click the `ROS1 Shell` icon on the desktop or the corresponding icon in the lower bar of the desktop to open the ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
roslaunch myarm_moveit demo.launch
``` 

The running effect is as follows:  

<img src =../../../resourse/12-ApplicationBaseROS/myarm_moveit.png
width ="500"  align = "center">

It can be planned and executed to demonstrate the effect:

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/12-ApplicationBaseROS/myarm_moveit.mp4" type='video/mp4' >
</video>


If you need to let the real robotic arm execute the plan synchronously, you need to open another ROS1 environment terminal:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-1.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.jpg
width ="500"  align = "center">
<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-3.jpg
width ="500"  align = "center">

Then run the command:

```bash
# The default serial port name of myArm-300 is "/dev/ttyAMA0", and the baud rate is 115200".
rosrun myarm_moveit sync_plan.py _port:=/dev/ttyAMA0 _baud:=115200
```

Then plan and execute again to demonstrate the effect:

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/12-ApplicationBaseROS/myarm_moveit.mp4" type='video/mp4' >
</video>