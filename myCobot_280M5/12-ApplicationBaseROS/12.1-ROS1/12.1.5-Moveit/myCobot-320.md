# Using MyCobot

`mycobot_ros` has integrated the MoveIt section.

Open the command line and run:

- 2022 mycobot 320-M5 version:
  
```bash
roslaunch new_mycobot_320_moveit mycobot320_moveit.launch
```

- 2022 mycobot 320-Pi version:
  
```bash
roslaunch new_mycobot_320_pi_moveit mycobot320_moveit.launch
```

The operation effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/12.2.7-9.jpg
width ="500"  align = "center">

If you want a real robot arm to execute a plan synchronously, you need to open another command line and run:

- 2022 mycobot 320-M5 version:
  
```bash
# The default serial port name of 2022 mycobot 320-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun new_mycobot_320_moveit sync_plan.py _port:=/dev/ttyUSB0 _baud:=115200
```
- 2022 mycobot 320-Pi version:
  
```bash
# The default serial port name of 2022 mycobot 320-Pi version is "/dev/ttyAMA0", and the baud rate is 115200.
rosrun new_mycobot_320_pi_moveit sync_plan.py _port:=/dev/ttyAMA0 _baud:=115200
```

# Modify motion speed

In order to prevent the joints from shaking during the movement of the real robotic arm, the movement speed of the joints needs to be reduced.

- In the `sync_plan.py` file, modify the speed parameter of the robot arm Python API, here it is changed to 25.
  
  ```python
  ...

  def callback(data):
    # rospy.loginfo(rospy.get_caller_id() + "%s", data)
    data_list = []
    for index, value in enumerate(data.position):
        radians_to_angles = round(math.degrees(value), 2)
        data_list.append(radians_to_angles)

    rospy.loginfo(rospy.get_caller_id() + "%s", data_list)
    mc.send_angles(data_list, 25)  # Change speed to 25

  ...

  ```

- In the Moveit RViz interface, modify the scaling ratio of speed and acceleration. Here, change it to 0.5, and then save the current configuration.

  <img src =../../../resourse/12-ApplicationBaseROS/12.1.4-19.png
width ="500"  align = "center">>