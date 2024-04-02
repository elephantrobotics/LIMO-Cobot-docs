# mira Moveit

`mycobot_ros` now integrates the MoveIt section.

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/12-ApplicationBaseROS/mira_moveit.mp4" type='video/mp4' >
</video>

Open the command line and run:

```bash
roslaunch mira_moveit mira_moveit.launch
```

The operation effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/12.1.4-2.png
width ="500"  align = "center">

If you need to synchronize the execution plan with the real robot arm, you need to open another command line and run:

```bash
# The default serial port name of Mira version is "/dev/ttyUSB0", and the baud rate is 115200".
rosrun mecharm_pi_moveit sync_plan.py
```
