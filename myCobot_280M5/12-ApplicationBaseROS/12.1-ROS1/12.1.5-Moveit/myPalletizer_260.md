# Mypalletizer 260 Moveit
`mypalletizer_260` has integrated the MoveIt section.

Open the command line and run:

- mypalletizer 260-M5 version:

```bash
roslaunch mypalletizer_260_moveit mypal_moveit.launch
```

- mypalletizer 260-Pi version:

```bash
roslaunch mypalletizer_260_pi_moveit mypal_moveit.launch
```


The operation effect is as follows:

<img src =../../../resourse/12-ApplicationBaseROS/mypal260/260moveit.png
width ="500"  align = "center">

If you want a real robot arm to execute a plan synchronously, you need to open another command line and run:

- mypalletizer 260-M5 version:

```bash
# The default serial port name of mypalletizer 260-M5 version is "/dev/ttyUSB0", and the baud rate is 115200. The serial port name of some models is "dev/ttyACM0". If the default serial port name is wrong, you can change the serial port name to "/dev/ttyACM0".
rosrun mypalletizer_260_moveit sync_plan.py _port:=/dev/ttyUSB0 _baud:=115200
```

- mypalletizer 260-Pi version:

```bash
# The default serial port name of the mypalletizer 260-Pi version is "/dev/ttyAMA0", and the baud rate is 1000000".
rosrun mypalletizer_260_pi_moveit sync_plan.py _port:=/dev/ttyAMA0 _baud:=1000000
```