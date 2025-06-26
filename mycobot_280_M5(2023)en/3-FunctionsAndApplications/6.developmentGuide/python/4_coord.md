## Coordinate control

It is mainly used to realize intelligent route planning to let the robot arm move from one position to another specified position. It is divided into `[x, y, z, rx, ry, rz]`, where `[x, y, z]` represents the position of the robot head in space (the coordinate system is the [rectangular coordinate system](https://zhidao.baidu.com/question/2125035227927850747.html)), and `[rx, ry, rz]` represents the posture of the robot head at this point (the coordinate system is the Euler coordinate system). The implementation of the algorithm and the representation of Euler coordinates require certain academic knowledge. We will not explain it too much here. As long as we understand the rectangular coordinate system, we can use this function well.

> **Note:** When setting coordinates, different series of robot arm joint structures are different. For the same set of coordinates, different series of robot arms will show different postures.
>
> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\axis/coordinate.jpg" style="zoom: 67%;" />


### Single parameter coordinate

**send_coord(id,coord,speed)**

- **Function:** Send a single coordinate value to the robot for movement
- **Parameter description:**
  - `id`: Represents the coordinate of the robot. Represented by numbers 1-6,for example, the X axis can be filled in 1, the Y can be filled in 2, and so on

  - `coord`: Enter the coordinate value you want to reach

  - `speed`: Indicates the speed of the robot movement, the range is 1-100
- **Return value:** 1

### Multi-parameter coordinates

**get_coords()**

- **Function:** Get current coordinates and posture
- **Return value:** `list` contains a list of coordinates and postures, length is 6, in order `[x, y, z, rx, ry, rz]`

**send_coords(coords, speed, mode)**

- **Function:** Send the overall coordinates and posture, and let the robot head move from the original point to the point you specify.
- **Parameter description:**
  - `coords`: [x,y,z,rx,ry,rz] coordinate value, length is 6

  - `speed`: Indicates the speed of the robot movement, the range is 1-100
  - `mode`: ( `int`): The value is limited to 0 and 1.
    - 0 means that the path of the robot head is nonlinear, that is, the route is randomly planned, as long as the robot head moves to the specified point while maintaining the specified posture.
    - 1 means that the path of the robot head is linear, that is, the intelligent planning route allows the robot head to move to the specified point in a straight line.
- **Return value:** 1

**set_tool_reference(coords)**

- **Function:** Set the tool coordinate system.
- **Parameter description:**
  - `coords`:
    - Six axes: [x,y,z,rx,ry,rz] coordinate values, length 6, x,y,z range -280 ~ 280, rx,ry,yz range -314 ~ 314
- **Return value:** 1

**get_tool_reference()**

- **Function:** Get the tool coordinate system.
- **Return value:** Return a coordinate list with a length of 6

**get_world_reference()**

- **Function:** Get the world coordinate system.
- **Return value:** Return a coordinate list with a length of 6

**set_world_reference(coords)**

- **Function:** Set the world coordinate system.
- **Parameter description:**
  - `coords`:
    - Six axes: [x,y,z,rx,ry,rz] coordinate values, length is 6, x,y,z range is -280 ~ 280, rx,ry,yz range is -314 ~ 314
- **Return value:** 1

**set_reference_frame(rftype)**

- **Function:** Set the base coordinate system.
- **Parameter description:**
  - `rftype`: 0 - base coordinate system (default), 1 - world coordinate system
- **Return value:** 1

**get_reference_frame()**

- **Function:** Get the base coordinate system.
- **Return value:** 0 - base coordinate system, 1 - world coordinate system, -1 - communication failed

**set_end_type(end)**

- **Function:** Set the end coordinate system.
- **Parameter description:**
  - `end`: 0 - flange (default), 1 - tool
- **Return value:** 1

**get_end_type()**

- **Function:** Get the end coordinate system.
- **Return value:** 0 - flange (default), 1 - tool, -1 - communication failed

### Example use

```python
from pymycobot.mycobot280 import MyCobot280
import time

# MyCobot280 class initialization requires two parameters:
# The first is the serial port string, such as:
    # linux: "/dev/ttyUSB0"
    # windows: "COM3"
    # The second is the baud rate:
    # M5 version: 115200
    # For example:
        # mycobot-M5:
            # linux:
            # mc = MyCobot280("/dev/ttyUSB0", 115200)
            # windows:
            # mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# The following is the object code for the Windows version
mc = MyCobot280("COM3", 115200)
# Get the current head coordinates and posture
coords = mc.get_coords()
print(coords)
# # Intelligently plan the route, so that the head reaches the coordinates [57.0, -107.4, 316.3] in a linear manner, and maintains the posture [-93.81, -12.71, -163.49], with a speed of 80mm/s
mc.send_coords([57.0, -107.4, 316.3, -93.81, -12.71, -163.49], 80, 1)

# Set the waiting time to 1.5 seconds
time.sleep(1.5)

# Intelligently plan the route, let the head reach the coordinates [-13.7, -107.5, 223.9] in a linear manner, and maintain the posture [165.52, -75.41, -73.52], with a speed of 80mm/s
mc.send_coords([-13.7, -107.5, 223.9, 165.52, -75.41, -73.52], 80, 1)

# Set the waiting time to 1.5 seconds
time.sleep(1.5)

# Only change the x coordinate of the head, set the x coordinate of the head to -40. Let it intelligently plan the route and move the head to the changed position, with a speed of 70mm/s
mc.send_coord(1, -40, 70)
```