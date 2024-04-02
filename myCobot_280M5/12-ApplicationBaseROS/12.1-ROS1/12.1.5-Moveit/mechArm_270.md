# mechArm 270 Moveit
`mycobot_ros` has integrated the MoveIt section.

Open the command line and run:

mechArm-M5 version:

```bash
roslaunch mecharm_moveit mecharm_moveit.launch
```

mechArm-PI version:

```bash
roslaunch mecharm_pi_moveit mecharm_moveit.launch
```

The operation effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/mecharm_moveit.png
width ="500"  align = "center">

If you want a real robot arm to execute a plan synchronously, you need to open another command line and run:

mechArm-M5 version:

```bash
# The default serial port name of the mechArm-M5 version is "/dev/ttyUSB0", and the baud rate is 115200". The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/ dev/ttyACM0".
rosrun mecharm_moveit sync_plan.py _port:=/dev/ttyUSB0 _baud:=115200
```

mechArm-PI version:

```bash
# The default serial port name of the mechArm version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mecharm_pi_moveit sync_plan.py _port:=/dev/ttyAMA0 _baud:=1000000
```