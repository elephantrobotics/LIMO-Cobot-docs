# Handle control

You can use the game controller to control the movement of the machine and use the gripper or suction pump to grab objects.

> Note: The handle needs to be purchased separately, please contact the official customer service for details

> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\handle/7.8.1.jpg" alt="7.1.1-1" style="zoom: 80%;" />

## The corresponding functions of the handle buttons are as follows:
### myCobot:

- **1**: RX coordinate value increases
- **2**: RX coordinate value decreases
- **3**: RY coordinate value decreases
- **4**: RY coordinate value increases
- **5**: X coordinate value increases
- **6**: X coordinate value decreases
- **7**: Y coordinate value decreases
- **8**: Y coordinate value increases
- **9**: Z coordinate value increases
- **10**: Z coordinate value decreases
- **11**: RZ coordinate value decreases
- **12**: RZ Coordinate value increases
- **13**: Wake up the handle. If the handle is not used for a long time after connection, it will enter sleep mode. You need to press this button to continue using it.
<!-- - **14**: Detect the machine connection status. The atom LED flashes green three times to indicate that the machine is normal, and flashes red three times to indicate abnormal status. -->
- **X**: Click the button to open the jaws
- **Y**: Click the button to close the jaws
- **A**: Click the button to turn on the suction pump
- **B**: Click the button to turn off the suction pump
- **Left 1**: Press and hold for 2s to initialize the robot to the joint zero position state.
- **Left 2**: Press and hold for 2s, the robot stops torque output and relaxes all joints.
- **Right 1**: Press and hold for 2s to initialize the robot to the initial point of movement.
- **Right 2**: Press and hold for 2s, the robot turns on torque output and all joints are locked.

# Instructions for use

## Connect the device

Connect MyCobot280 and the handle to the computer.

## Install the required packages

Download code: https://github.com/elephantrobotics/pymycobot

Open the terminal, switch the path to the `pymycobot/demo/handle_control` folder, and run the following command:

```bash
pip3 install -r requirements.txt
```

## Change the port number

### myCobot

Edit the handle_control.py file

```python
import pygame
import time
from pymycobot import MyCobot280
import threading
# Change com7 to the actual port number detected by your computer

mc = MyCobot280("com7", 115200)
...
```
Run the program.

```bash
python3 myCobot280_handle_control.py
```

> Note: After running the program, first click the **Right 1** button. After the machine reaches the initial point, other operations can be performed.