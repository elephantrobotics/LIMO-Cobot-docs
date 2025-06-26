# Draw a pattern

You can control the movement of the robot arm and realize the drawing operation by parsing the instructions in a gcode file.

## Installation diagram

> Note: The end of the robot arm and the pen clip are connected using Lego technology.

> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\draw/7.15.2.jpg" alt="7.1.1-1" style="zoom: 80%;" />

## Instructions

### 1. Connect the device

Connect MyCobot280 to the computer, install the pen clip to the end of the robot arm, put the signature pen in the pen clip and tighten the screws to fix it.

> Note: Use the G-type base 2.0 to fix the robot arm on the desktop, and place the A4 white paper on the desktop for drawing patterns.

### 2. Install the required packages

Download code: https://github.com/elephantrobotics/pymycobot

Open the terminal, switch the path to the `pymycobot/demo/myCobot_280_demo` folder, and run the following command:

```bash
pip install pyserial pymycobot
```

### 3. Change the port number

Edit the 280_draw_gcode.py file

```python
# Change COM14 to the actual port number detected by your computer
import time
from pymycobot import MyCobot280 # import mycobot library,if don't have, first 'pip install pymycobot'

# use PC and M5 control
mc = MyCobot280('COM14', 115200) # WINDOWS use, need check port number when you PC
# mc = MyCobot280('/dev/ttyUSB0',115200) # VM linux use
time.sleep(0.5)
...
```
Just run the program.

```bash
python 280_draw_gcode.py
```

Then, according to the terminal prompt, enter different numbers to select different patterns:

```bash
1-square
2-triangle
3-five point star
4-quit
```

> Note: The initial point of the robot arm can be changed by yourself, but the posture of the J6 joint must be vertically downward, and the speed can also be changed by yourself, the default is 100 mm per second.

```python
# Send the initial point angle of the robot arm, the speed is 50,
# it can be customized and modified, as long as the end is facing down
mc.send_angles([0, -40, -130, 80, 0, 50], 50)
# Wait 3 seconds for the robot arm to move to the specified angle
time.sleep(3)
# Get the current coordinates of the robot arm
get_coords = mc.get_coords()
time.sleep(1.5)
# Save the parsed coordinates
data_coords = []
# Set the drawing speed to 100, and the speed range is 0~100
draw_speed = 100

...

```