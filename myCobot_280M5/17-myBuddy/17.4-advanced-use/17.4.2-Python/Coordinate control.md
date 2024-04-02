# Coordinate control

It is mainly used to realize intelligent route planning to make the robot arm move from one position to another specified position. It is divided into `[x, y, z, rx, ry, rz]`. Among them `[x,y,z]` represents the position of the robot arm head in space (The coordinate system is [Cartesian coordinate system](https://zhidao.baidu.com/question/2125035227927850747.html)); `[rx,ry,rz]` represents the posture of such head at this point (The coordinate system is Euler coordinates). The realization of the algorithm and the representation of Euler coordinates require a certain degree of academic knowledge. We will not explain it too much here. We can use this function well as long as we understand the Cartesian coordinate system.

> **Note:** When setting the coordinates, different series of manipulators have different joint structures. For the same set of coordinates, different series of manipulators will show different postures.

![7.3-1](../../../resourse/7-ApplicationBasePython/7.3-1.jpg)

# One-parameter coordinates

### send_coord(id, coord, data, speed)

Send a single coordinate to the robotic arm

* **Parameters**

  * **id** – 1/2/3 (L/R/W).

  * **coord** – 1 ~ 6 (x/y/z/rx/ry/rz)

  * **data** – Coordinate value

  * **speed** – 0 ~ 100

### get_coord(id, joint_id)

Read a single coordinate parameter

* **Parameters**

  * **id** (_int_) – 1/2/3 (L/R/W).

  * **joint_id** (_int_) – 1 - 7 (7 is gripper)

# Multiparameter Coordinates

### send_coords(id, coords, speed, mode)

Send all coords to robot arm.

* **Parameters**

  * **id** – 1/2 (L/R).

  * **coords** – a list of coords value(List[float]), length 6, [x(mm), y, z, rx(angle), ry, rz]

  * **speed** – (int) 0 ~ 100

  * **mode** – (int) 0 - moveJ, 1 - moveL, 2 - moveC

# Case1

```python
from pymycobot.mybuddy import MyBuddy
import time
mc = MyBuddy("/dev/ttyACM0", 115200)

# Get the coordinates and posture of the current head of the left arm
coords = mc.get_coords(1)
print(coords)

# Intelligently plan the route, let the head reach the coordinates of [57.0, -107.4, 316.3] in a linear manner, and maintain the attitude of [-93.81, -12.71, -163.49], and the speed is 80mm/s
mc.send_coords(1, [57.0, -107.4, 316.3, -93.81, -12.71, -163.49], 80, 1)

time.sleep(1.5)

# Intelligently plan the route, let the head reach the coordinates of [-13.7, -107.5, 223.9] in a linear manner, and maintain the attitude of [165.52, -75.41, -73.52], with a speed of 80mm/s
mc.send_coords(1, [-13.7, -107.5, 223.9, 165.52, -75.41, -73.52], 80, 1)

time.sleep(1.5)

# To change only the x-coordinate of the head of the left arm, set the x-coordinate of the head to -40. Let it plan the route intelligently and move the head to the changed position, with a speed of 70mm/s
mc.send_coord(1, 1, -40, 70)
```