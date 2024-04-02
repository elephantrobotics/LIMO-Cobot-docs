# Control of the robotic arm

## 1 Slider Control

Open a command line and run:

```bash
# The default IP of mycobot pro 600 is "192.168.10.159" and the port number is 5001. The specific IP is subject to the network connected to the actual robot arm.
ros2 launch mycobot_600 slider_control.launch.py ip:=192.168.10.159 port:=5001
```

**rviz and a slider component will be opened**, and you will see the following interface:

<img src =../../../resourse/12-ApplicationBaseROS/600_ros2_slider.png
width ="500"  align = "center">

Then you can **control the model in rviz to make it move by dragging the slider**. Real robots will follow the move.


**Note: Since the robot arm will move to the current position of the model when the command is input, make sure that the model in rviz does not appear to be worn out before you use the command.**

**Do not drag the slider quickly after connecting the robot arm to prevent damage to the robot arm**.