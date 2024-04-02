# Using MyCobot

`mycobot_ros` has integrated the MoveIt section.

Open the command line and run:

- mycobot 280-M5 version:
  
```bash
roslaunch mycobot_280_moveit mycobot_moveit.launch
```

- mycobot 280-Pi version:
  
```bash
roslaunch mycobot_280_moveit mycobot_moveit.launch
```

- mycobot 280-JetsonNano version:

```bash
roslaunch mycobot_280jn_moveit mycobot_moveit.launch
```

- mycobot 280-Arduino version:

```bash
roslaunch mycobot_280arduino_moveit mycobot_moveit.launch
```

The operation effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/moveit-1.png
width ="500"  align = "center">

can be planned and executed to demonstrate the effect:

<img src =../../../resourse/12-ApplicationBaseROS/moveit-2.gif
width ="500"  align = "center">

If you want a real robot arm to execute a plan synchronously, you need to open another command line and run:

- mycobot 280-M5 version:
  
```bash
# The default serial port name of mycobot 280-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mycobot_280_moveit sync_plan.py _port:=/dev/ttyUSB0 _baud:=115200
```
- mycobot 280-Pi version:
  
```bash
# The default serial port name of mycobot 280-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000.
rosrun mycobot_280_moveit sync_plan.py _port:=/dev/ttyAMA0 _baud:=1000000
```

- mycobot 280-JetsonNano version:

```bash
# The default serial port name of mycobot 280-JetsonNano version is "/dev/ttyTHS1", and the baud rate is 1000000.
rosrun mycobot_280jn_moveit sync_plan.py _port:=/dev/ttyTHS1 _baud:=1000000
```

- mycobot 280-Arduino version:

```bash
# The default serial port name of mycobot 280-Arduino version is "/dev/ttyACM0", and the baud rate is 115200.
rosrun mycobot_280arduino_moveit sync_plan.py _port:=/dev/ttyACM0 _baud:=115200
```
