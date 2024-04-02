# Joint control

For a serial multi-joint robot, the control of the joint space is to control the variables of each joint so as to make each joint reaches a target position at a certain speed.

> **Notice:** When setting the angle, the values corresponding to different manipulators are different. For the specific limit value, please refer to the parameter introduction of the corresponding manipulator.

# single joint control

### send_angle(id, joint, angle, speed)

Send one degree of joint to robot arm.

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint** – 1 ~ 6

  - **angle** – int

  - **speed** – 1 ~ 100

- **Returns**
  - None

### get_angle(id, joint_id)

Get the angle of a single joint

* **Parameters**

  * **id** (_int_) – 1/2/3 (L/R/W).

  * **joint_id** (_int_) – 1 - 7 (7 is gripper)

### set_encoder(id, joint_id, encoder, speed)

Set a single joint rotation to the specified potential value.

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – 1 - 6.

  - **encoder** – The value of the set encoder.

- **Returns**
  - None

# multi-joint control

### get_angles(id)

Get the degree of all joints.

- **Parameters**

    **id** – 1/2 (L/R)

- **Returns**

    A float list of all degree.

- **Return type**

    list

### send_angles(id, degrees, speed)

Send all angles to the robotic arm

- **Parameters**

  - **id** – 1/2 (L/R).

  - **degrees** – [angle_list] len 6

  - **speed** – 1 - 100

### set_encoders(id, encoders, speed)

Set the six joints of the manipulator to execute synchronously to the specified position.

- **Parameters**

  - **id** – 1/2 (L/R).

  - **encoders** – A encoder list, length 6.

  - **speed** – speed 1 ~ 100

### get_radians(id)

Get the radians of all joints

- **Parameters**

    **id** – 1/2 (L/R)

- **Returns**

    A list of float radians [radian1, …]

- **Return type**

    list

### send_radians(id, radians, speed)

Send the radians of all joints to robot arm

* **Parameters**

  * **id** – 1/2 (L/R).

  * **radians** – a list of radian values( List[float]), length 6

  * **speed** – (int )1 ~ 100

# case1

```python
from pymycobot.mybuddy import MyBuddy
import time
mc = MyBuddy("/dev/ttyACM0", 115200)

# Send angles to the six joints of the left arm
mc.send_angles(1, [0, 0, 0, 0, 0, 0], 50)
time.sleep(3)

# Send the angle to the first joint of the left arm
mc.send_angle(1, 1, 90, 50)
time.sleep(2)

# Get the joint angle of the left arm
angles = mc.get_angles(1)
print("left angles: ",angles)

# Relax all joints of the left arm. Before running this command, please support the left arm with your hand to prevent it from falling suddenly
mc.release_all_servos(1)
```