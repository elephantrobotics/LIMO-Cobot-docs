# MyCobot 280

[toc]

## Python API usage instaructions

API (Application Programming Interface), also known as Application Programming Interface functions, are predefined functions. When using the following function interfaces, please import our API library at the beginning by entering the following code, otherwise it will not run successfully:

```python
# Example
from pymycobot import MyCobot280

mc = MyCobot280('COM3')

# Gets the current angle of all joints
angles = mc.get_angles()
print(angles)

# Set 1 joint to move to 40 and speed to 20
mc.send_angle(1, 40, 20)
```

>>**Note:** Some function interfaces have return values, but if you enter the code directly, the result returned is no return value. You need to use the print function to print out the result. For example, if you want to get the current angle value of the robot arm, you can use get_angles(), but directly entering this function will not give you any result. The correct way to write it is: print(get_angles()) to print out the speed value. If the API description below indicates that there is no return value, you do not need to use the print function. Otherwise, you need to use the print function to print the result.

### 1. System Status

#### 1.1 `get_system_version()`

- **function：** get system version
- **Return value：** system version

#### 1.2 `get_basic_version()`

- **function：** Get basic firmware version for M5 version
- **Return value：** `float` firmware version

#### 1.3 `get_error_information()`

- **function：** Obtaining robot error information

- **Return value：** 
    - 0: No error message.
    - 1 ~ 6: The corresponding joint exceeds the limit position.
    - 16 ~ 19: Collision protection.
    - 32: Kinematics inverse solution has no solution.
    - 33 ~ 34: Linear motion has no adjacent solution.

#### 1.4 `clear_error_information()`

- **function:** Clear robot error message

### 2. Overall Status

#### 2.1 `power_on()`

- **function:** atom open communication (default open)

- **Return value:**
  - `1` - Power on completed.

#### 2.2 `power_off()`

- **function:** Power off of the robotic arm

- **Return value:**
  - `1` - Power on completed.

#### 2.3 `is_power_on()`

- **function:** judge whether robot arms is powered on or not

- **Return value:**
  - `1`: power on
  - `0`: power off
  - `-1`: error

#### 2.4 `release_all_servos()`

- **function:** release all robot arms
  - Attentions：After the joint is disabled, it needs to be enabled to control within 1 second
- **Parameters**：`data`（optional）：The way to relax the joints. The default is damping mode, and if the 'data' parameter is provided, it can be specified as non damping mode (1- Undamping).
- **Return value:**
  - `1` - release completed.

#### 2.5 `focus_servo(servo_id)`

- **function:** Power on designated servo

- **Parameters:** 
  - `servo_id:` int, 1-6

- **Return value:**
  - `1`: complete

#### 2.6 `is_controller_connected()`

- **function:** Wether connected with Atom

- **Return value:**
  - `1`: succeed
  - `0`: failed
  - `-1`: error data

#### 2.7 `read_next_error()`

- **function:** Robot Error Detection

- **Return value:** list len 6
  - `0`: No abnormality
  - `1`: Communication disconnected
  - `2`: Unstable communication
  - `3`: Servo abnormality
  
#### 2.8 `get_fresh_mode()`

- **function:** Query sports mode

- **Return value:** 
  - `0`: Interpolation mode
  - `1`: Refresh mode

#### 2.9 `set_fresh_mode()`

- **function:** Set command refresh mode
  
- **Parameters:**
  - `1`: Always execute the latest command first.
  - `0`: Execute instructions sequentially in the form of a queue.

- **Return value:** 
  - `1`: complete

#### 2.10 `set_free_mode()`

- **function:** set to free mode
  
- **Parameters:**
  - `1`: open free mode
  - `0`: close free mode

- **Return value:** 
  - `1`: complete

#### 2.11 `is_free_mode()`

- **function:** Check if it is free mode

- **Return value:** 
  - `1`: free mode
  - `0`: on-free mode

#### 2.12 `focus_all servos()`

- **Function:** All servos are powered on

- **Return value:**
  - `1`: complete

#### 2.13 `set_vision_mode()`

- **Function:** Set the vision tracking mode, limit the attitude flip of send_coords in refresh mode. (Applicable only to vision tracking function)

- **Parameter:**
  - `1`: open
  - `0`: close

- **Return value:**
  - `1`: complete

### 3.MDI Mode and Operation

#### 3.1 `get_angles()`

- **function:** get the degree of all joints
- **Return value**: `list  `a float list of all degree

#### 3.2 `send_angle(id, degree, speed)`

- **function:** send one degree of joint to robot arm
- **Parameters:**
  - `id`: Joint id, range int 1-6
  - `degree`: degree value(`float`)

    <table>
      <tr>
             <th>Joint Id</th>
             <th>Range</th>
      </tr>
      <tr>
             <td text-align: center>1</td>
             <td>-168 ~ 168</td>
      </tr>
      <tr>
             <td>2</td>
             <td>-135 ~ 135</td>
      </tr>
      <tr>
             <td>3</td>
             <td>-150 ~ 150</td>
      </tr>
        <tr>
             <td>4</td>
             <td> -145 ~ 145</td>
      </tr>
      <tr>
             <td>5</td>
             <td>-165 ~ 165</td>
      </tr>
      <tr>
             <td>6</td>
             <td>-180 ~ 180</td>
      </tr>
    </table>

  - `speed`：the speed and range of the robotic arm's movement 1~100
- **Return value:** 
  - `1`: complete

#### 3.3 `send_angles(angles, speed)`

- **function：** Send all angles to all joints of the robotic arm
- **Parameters:**
  - `angles`: a list of degree value(`List[float]`), length 6
  - `speed`: (`int`) 1 ~ 100
- **Return value:** 
  - `1`: complete

#### 3.4 `get_coords()`

- **function:** Obtain robot arm coordinates from a base based coordinate system
- **Return value:** a float list of coord:[x, y, z, rx, ry, rz]

#### 3.5 `send_coord(id, coord, speed)`

- **function:** send one coord to robot arm
- **Parameters:**
  - `id`:send one coord to robot arm, 1-6 corresponds to [x, y, z, rx, ry, rz]
  - `coord`: coord value(`float`)

<table>
  <tr>
         <th>Coord ID</th>
         <th>Range</th>
  </tr>
  <tr>
         <td text-align: center>x</td>
         <td>-281.45 ~ 281.45</td>
  </tr>
  <tr>
         <td>y</td>
         <td>-281.45 ~ 281.45</td>
  </tr>
  <tr>
         <td>z</td>
         <td>-70 ~ 412.67</td>
  </tr>
    <tr>
         <td>rx</td>
         <td> -180 ~ 180</td>
  </tr>
  <tr>
         <td>ry</td>
         <td>-180 ~ 180</td>
  </tr>
  <tr>
         <td>rz</td>
         <td>-180 ~ 180</td>
  </tr>
</table>

  - `speed`: (`int`) 1-100
- **Return value:** 
  - `1`: complete

#### 3.6 `send_coords(coords, speed, mode)`

- **function:**: Send overall coordinates and posture to move the head of the robotic arm from its original point to your specified point
- **Parameters:**
  - coords: ： a list of coords value `[x,y,z,rx,ry,rz]`,length6
  - speed`(int)`: 1 ~ 100
  - mode: `(int)` 0 - angluar, 1 - linear
- **Return value:** 
  - `1`: complete

#### 3.7 `pause()`

- **function:** Control the instruction to pause the core and stop all movement instructions
- **Return value**:
  - `1` - stopped
  - `0` - not stop
  - `-1` - error

#### 3.8 `sync_send_angles(angles, speed, timeout=15)`

- **function：** Send the angle in synchronous state and return when the target point is reached
- **Parameters:**
  - `angles`: a list of degree value(`List[float]`), length 6
  - `speed`: (`int`) 1 ~ 100
  - `timeout`: default 15 seconds
- **Return value:**
  - `1`: complete

#### 3.9 `sync_send_coords(coords, speed, mode=0, timeout=15)`

- **function：** Send the coord in synchronous state and return when the target point is reached
- **Parameters:**
  - `coords`: a list of coord value(`List[float]`), length 6
  - `speed`: (`int`) 1 ~ 100
  - `mode`: (`int`) 0 - angular（default）, 1 - linear
  - `timeout`: default 15 seconds
- **Return value:**
  - `1`: complete

#### 3.10 `get_angles_coords()`

- **function：** Get joint angles and coordinates

- **Return value:** A list with a length of 12. The first six digits are angle information, and the last six digits are coordinate information. 

#### 3.11 `is_paused()`

- **function:** Check if the program has paused the move command
- **Return value:**
  - `1` - paused
  - `0` - not paused
  - `-1` - error

#### 3.12 `resume()`

- **function:** resume the robot movement and complete the previous command
- **Return value:**
  - `1` - complete

#### 3.13 `stop()`

- **function:** stop all movements of robot
- **Return value**:
  - `1` - stopped
  - `0` - not stop
  - `-1` - error

#### 3.14 `is_in_position(data, flag)`

- **function** : judge whether in the position.
- **Parameters:**
  - data: Provide a set of data that can be angles or coordinate values. If the input angle length range is 6, and if the input coordinate value length range is 6
  - flag data type (value range 0 or 1)
    - `0`: angle
    - `1`: coord
- **Return value**:
  - `1` - true
  - `0` - false
  - `-1 ` - error

#### 3.15 `is_moving()`

- **function:** judge whether the robot is moving
- **Return value:**
  - `1` moving
  - `0` not moving
  - `-1` error

#### 3.16 `angles_to_coords(angles)`

- **Function** : Convert angles to coordinates.
- **Parameters:**
  - `angles`: `list` List of floating points for all angles.
- **Return value**: `list` List of floating points for all coordinates.

#### 3.17 `solve_inv_kinematics(target_coords, current_angles)`

- **Function** : Convert coordinates to angles.
- **Parameters:**
  - `target_coords`: `list` List of floating points for all coordinates.
  - `current_angles`: `list` List of floating points for all angles, current angles of the robot
- **Return value**: `list` List of floating points for all angles.

### 4. JOG Mode and Operation

#### 4.1 `jog_angle(joint_id, direction, speed)`

- **function:** jog control angle
- **Parameters**:
  - `joint_id`: Represents the joints of the robotic arm, represented by joint IDs ranging from 1 to 6
  - `direction(int)`: To control the direction of movement of the robotic arm, input `0` as negative value movement and input `1` as positive value movement
  - `speed`: 1 ~ 100
- **Return value:**
  - `1`: complete

#### 4.2 `jog_coord(coord_id, direction, speed)`

- **function:** jog control coord.
- **Parameters:**
  - `coord_id`: (`int`) Coordinate range of the robotic arm: 1~6
  - `direction`: (`int`) To control the direction of machine arm movement, `0` - negative value movement, `1` - positive value movement
  - `speed`: 1 ~ 100
- **Return value:**
  - `1`: complete

#### 4.3 `jog_rpy(end_direction, direction, speed)`

- **function:** Rotate the end around a fixed axis in the base coordinate system
- **Parameters:**
  - `end_direction`: (`int`) Roll, Pitch, Yaw (1-3)
  - `direction`: (`int`) To control the direction of machine arm movement, `1` - forward rotation, `0` - reverse rotation
  - `speed`: (`int`) 1 ~ 100
- **Return value:**
  - `1`: complete

#### 4.4 `jog_increment_angle(joint_id, increment, speed)`

- **Function**: Angle stepping, single joint angle increment control
- **Parameter**:
  - `joint_id`: 1-6
  - `increment`: Incremental movement based on the current position angle
  - `speed`: 1~100
- **Return value:**
  - `1`: Completed

#### 4.5 `jog_increment_coord(id, increment, speed)`

- **Function**: Coordinate stepping, single coordinate increment control
- **Parameter**:
  - `id`: Coordinate axis 1-6
  - `increment`: Incremental movement based on the current position coordinate
  - `speed`: 1~100
- **Return value:**
  - `1`: Completed

#### 4.6 `set_encoder(joint_id, encoder, speed)`

- **function**: Set a single joint rotation to the specified potential value

- **Parameters**

  - `joint_id`: (`int`) 1-6
  - `encoder`: 0 ~ 4096
  - `speed`: 1 ~ 100
- **Return value:**
  - `1`: complete

#### 4.7 `get_encoder(joint_id)`

- **function**: Set a single joint rotation to the specified potential value

- **Parameters**

  - `joint_id`: (`int`) 1-6

- **Return value:** (`int`) Joint potential value

#### 4.8 `set_encoders(encoders, speed)`

- **function**: Set the six joints of the manipulator to execute synchronously to the specified position.

- **Parameters**

  - `joint_id`: (`int`) 1-6
  - `encoder`: 0 ~ 4096
  - `speed`: 1 ~ 100
- **Return value:**
  - `1`: complete

#### 4.9 `get_encoders()`

- **function**: Get the six joints of the manipulator.

- **Return value:** (`list`) the list of encoders

### 5. Running status and Settings

#### 5.1 `get_joint_min_angle(joint_id)`

- **function:** Gets the minimum movement angle of the specified joint
- **Parameters:**
  - ` joint_id` : Enter joint ID (range 1-6)
- **Return value**：`float` Angle value

#### 5.2 `get_joint_max_angle(joint_id)`

- **function:** Gets the maximum movement angle of the specified joint
- **Parameters:**
  - ` joint_id` : Enter joint ID (range 1-6)
- **Return value:** `float` Angle value

#### 5.3 `set_joint_min(id, angle)`

- **function:** Set minimum joint angle limit
- **Parameters:**
  - `id` : Enter joint ID (range 1-6)
  - `angle`: Refer to the limit information of the corresponding joint in the [send_angle()](#32-send_angleid-degree-speed) interface, which must not be less than the minimum value
- **Return value:**
  - `1`: complete

#### 5.4 `set_joint_max(id, angle)`

- **function:** Set maximum joint angle limit
- **Parameters:**
  - `id` : Enter joint ID (range 1-6)
  - `angle`: Refer to the limit information of the corresponding joint in the [send_angle()](#32-send_angleid-degree-speed) interface, which must not be greater than the maximum value
- **Return value:**
  - `1`: complete
  
### 6. Joint motor control

#### 6.1 `is_servo_enable(servo_id)`

- **function:** Detecting joint connection status
- **Parameters:** `servo id` 1-6
- **Return value:**
  - `1`: Connection successful
  - `0`: not connected
  - `-1`: error

#### 6.2 `is_all_servo_enable()`

- **function:** Detect the status of all joint connections
- **Return value:**
  - `1`: Connection successful
  - `0`: not connected
  - `-1`: error

#### 6.3 `set_servo_calibration(servo_id)`

- **function:** The current position of the calibration joint actuator is the angle zero point
- **Parameters**:
  - `servo_id`: 1 - 6
- **Return value:**
  - `1`: complete

#### 6.4 `release_servo(servo_id)`

- **function:** Set the specified joint torque output to turn off
- **Parameters**:
  - `servo_id`: 1 ~ 6
- **Return value:**
  - `1`: release successful
  - `0`: release failed
  - `-1`: error

#### 6.5 `focus_servo(servo_id)`

- **function**: Set the specified joint torque output to turn on
- **Parameters**: `servo_id`: 1 ~ 6
- **Return value:**
  - `1`: focus successful
  - `0`: focus failed
  - `-1`: error

#### 6.6 `set_servo_data(servo_id, data_id,  value, mode=None）`

- **function:** Set the data parameters of the specified address of the steering gear
- **Parameters**：
  - `servo_id`: (`int`) joint id 1 - 6
  - `data_id`: (`int`) Data address
  - `value`: (`int`) 0 - 4096
  - `mode`: 0 - indicates that value is one byte(default), 1 - 1 represents a value of two bytes.
- **Return value:** 
  - `1`: complete

#### 6.7 `get_servo_data(servo_id, data_id, mode=None）`

- **function:** Read the data parameter of the specified address of the steering gear.
- **Parameters**：
  - `servo_id`: (`int`) joint id 1 - 6
  - `data_id`: (`int`) Data address
  - `mode`: 0 - indicates that value is one byte(default), 1 - 1 represents a value of two bytes.
- **Return value:** 0 ~ 4096

#### 6.8 `joint_brake(joint_id）`

- **function:** Make it stop when the joint is in motion, and the buffer distance is positively related to the existing speed
- **Parameters**：
  - `joint_id`: (`int`) joint id 1 - 6

- **Return value:**
  - `1`: complete

### 7. 9g Servo

#### 7.1 `move_round()`

- **function**：Drive the 9g steering gear clockwise for one revolution
- **Return value**：
  - `1`: complete

#### 7.2 `set_four_pieces_zero()`

- **function**：Set the zero position of the four-piece motor
- **Return value**：
  - `1`: success
  - `0`: failed

### 8. Servo state value

#### 8.1 `get_servo_speeds()`

- **function**：Get the movement speed of all joints
- **Return value**： A list unit step/s

#### 8.2 `get_servo_voltages()`

- **function**：Get joint voltages
- **Return value**： A list volts < 24 V

#### 8.3 `get_servo_status()`

- **function**：Get the movement status of all joints
- **Return value**： A list,[voltage, sensor, temperature, current, angle, overload], a value of `0` means no error, a value of `1` indicates an error

#### 8.4 `get_servo_temps()`

- **function**：Get joint temperature
- **Return value**： A list unit ℃

### 9. Robotic arm end IO control

#### 9.1 `set_color(r, g, b)`

- **function**: Set the color of the end light of the robotic arm

- **Parameters**:

  - `r (int)`: 0 ~ 255

  - `g (int)`: 0 ~ 255

  - `b (int)`: 0 ~ 255
- **Return value**：
  - `1`: complete
  
#### 9.2 `set_digital_output(pin_no, pin_signal)`

- **function:** set IO statue
- **Parameters**
  - `pin_no` (int): Pin number
  - `pin_signal` (int): 0 / 1
- **Return value**：
  - `1`: complete

#### 9.3 `get_digital_input(pin_no)`

- **function:** read IO statue
- **Parameters**: `pin_no` (int)
- **Return value**: signal

#### 9.4 `set_pin_mode(pin_no, pin_mode)`

- **function:** Set the state mode of the specified pin in atom.
- **Parameters**
  - `pin_no` (int): Pin number
  - `pin_mode` (int): 0 - input, 1 - output, 2 - input_pullup
- **Return value**：
  - `1`: complete

### 10. Robotic arm end gripper control

#### 10.1 `set_gripper_state(flag, speed, _type_1=None)`

- **function**: Adaptive gripper enable

- **Parameters**:

  - `flag (int) `: 0 - open 1 - close, 254 - release

  - `speed (int)`: 0 ~ 100

  - `_type_1 (int)`:

    - `1` : Adaptive gripper (default state is 1)

    - `2` : A nimble hand with 5 fingers

    - `3` : Parallel gripper

    - `4` : Flexible gripper
- **Return value**：
  - `1`: complete

#### 10.2 `set_gripper_value(gripper_value, speed, gripper_type=None)`

- **function**: Set the gripper value

- **Parameters**:

  - `gripper_value (int) `: 0 ~ 100

  - `speed (int)`: 0 ~ 100

  - `gripper_type (int)`:

    - `1` : Adaptive gripper (default state is 1)

    - `2` : A nimble hand with 5 fingers

    - `3` : Parallel gripper

    - `4` : Flexible gripper
- **Return value**：
  - `1`: complete

#### 10.3 `set_gripper_calibration()`

- **function**: Set the current position of the gripper to zero
- **Return value**：
  - `1`: complete

#### 10.4 `is_gripper_moving()`

- **function**: Judge whether the gripper is moving or not
- **Return value**：
  - `0`: not moving
  - `1`: is moving
  - `-1`: error data

#### 10.5 `get_gripper_value()`

- **function**: Get the value of gripper
- **Parameters**:
  - `gripper_type`: (int) default 1
    - 1: Adaptive gripper
    - 3: Parallel gripper
    - 4: Flexible gripper
- **Return value**：gripper value (int)
  
#### 10.6 `set_pwm_output(channel, frequency, pin_val)`

- **function**: PWM control
- **Parameters**:
  - `channel` : (int): IO number.
  - `frequency`: (int): clock frequency
  - `pin_val`: (int) Duty cycle 0 ~ 256; 128 means 50%
- **Return value**：
  - `1`: complete

#### 10.7 `set_HTS_gripper_torque(torque)`

- **function**: Set new adaptive gripper torque
- **Parameters**: 
  - `torque`: (int): 150 ~ 980
- **Return value**:
  - `0`: Set failed
  - `1`: Set successful

#### 10.8 `get_HTS_gripper_torque()`

- **function**: Get gripper torque
- **Return value**:  (int) 150 ~ 980

#### 10.9 `get_gripper_protect_current()`

- **function**: Get the gripper protection current
- **Return value**:  (int) 1 ~ 500

#### 10.10 `set_gripper_protect_current(current)`

- **function**: Set the gripper protection current
- **Parameters**: 
  - `current`: (int): 1 ~ 500
- **Return value**:
  - `1`: complete

#### 10.11 `init_gripper()`

- **function**: Initialize gripper
- **Return value**: 
  - `1`: complete

#### 10.12 `gripper_stop()`

- **Function**: Stop gripper movement
- **Return value**:
- `1`: Completed

### 11. Set bottom IO input/output status

#### 11.1 `set_basic_output(pin_no, pin_signal)`

- **function**：Set Base IO Output
- **Parameters**：
  - `pin_no` (`int`) Pin port number
  - `pin_signal` (`int`): 0 - low. 1 - high

#### 11.2 `get_basic_input(pin_no)`

- **function:** Read base IO input
- **Parameters:**
  - `pin_no` (`int`) pin number
- **Return value:** 0 - low. 1 - high

### 12. WLAN Setting

#### 12.1 `set_ssid_pwd(account, password)`

- **function:** Change connected wifi. (Apply to m5)
- **Parameters:**
  - `account` (`str`) new wifi account
  - `password` (`str`) new wifi password
- **Return value:**
   - `1`: complete

#### 12.2 `get_ssid_pwd()`

- **function:** Get connected wifi account and password. (Apply to m5)
- **Return value:** (account, password)

#### 12.3 `set_server_port(port)`

- **function:** Change the connection port of the server
- **Parameters:**
  - `port` (`int`) The new connection port of the server.
- **Return value:**
   - `1`: complete

### 13. TOF

#### 13.1 `get_tof_distance()`

- **function:** Get the detected distance (Requires external distance detector)
- **Return value:** (int) The unit is mm.

### 14. Communication mode

#### 14.1 `set_transponder_mode(mode)`

- **function:** Set basic communication mode
- **Parameters:**
  - `mode` : 0 - Turn off transparent transmission，1 - Open transparent transmission
- **Return value:**
   - `1`: complete

#### 14.2 `get_transponder_mode()`

- **function:** Get basic communication mode
- **Parameters:**
- **Return value:**
   - `1`: Open transparent 
   - `0`: Turn off transparent transmission

### 15. Cartesian space coordinate parameter setting

#### 15.1 `set_tool_reference(coords)`

- **function:** Set tool coordinate system.
- **Parameters**：
  - `coords`: (`list`) [x, y, z, rx, ry, rz].
- **Return value:** 
  - `1`: complete

#### 15.2 `get_tool_reference(coords)`

- **function:** Get tool coordinate system.
- **Return value:** (`list`) [x, y, z, rx, ry, rz]

#### 15.3 `set_world_reference(coords)`

- **function:** Set world coordinate system.
- **Parameters**：
  - `coords`: (`list`) [x, y, z, rx, ry, rz].
- **Return value:** 
  - `1`: complete

#### 15.4 `get_world_reference()`

- **function:** Get world coordinate system.
- **Return value:** `list` [x, y, z, rx, ry, rz].

#### 15.5 `set_reference_frame(rftype)`

- **function:** Set base coordinate system.
- **Parameters：**`rftype`: 0 - base 1 - tool.
- **Return value:**
   - `1`: complete

#### 15.6 `get_reference_frame()`

- **function:** Get base coordinate system.
- **Return value:** (`list`) [x, y, z, rx, ry, rz].

#### 15.7 `set_movement_type(move_type)`

- **function:** Set movement type.
- **Parameters**：
  - `move_type`: 1 - movel, 0 - moveJ.
- **Return value:**
   - `1`: complete

#### 15.8 `get_movement_type()`

- **function:** Get movement type.
- **Return value:**
  - `1` - movel
  - `0` - moveJ

#### 15.9 `set_end_type(end)`

- **function:** Set end coordinate system
- **Parameters:**
  - `end (int)`: `0` - flange, `1` - tool
- **Return value:**
   - `1`: complete

#### 15.10 `get_end_type()`

- **function:** Obtain the end coordinate system
- **Return value:**
  - `0` - flange
  - `1` - tool

### 16. utils (module)

This module supports some helper methods. Use the code entered at the beginning of the file to import the module:

```python
from pymycobot import utils
```

#### 16.1 `utils.get_port_list()`

- **Function**: Get a list of all current serial port numbers

- **Return value:** Serial port list (`list`)

#### 16.2 `utils.detect_port_of_basic()`

- **Function**: Return the first detected serial port number of M5 Basic. (Only one serial port number will be returned)

- **Return value:** Return the detected port number. If no serial port number is detected, it will return: None

## MyCobot 280 Socket

> Note:
> The robotic arm that uses this class of premise has a server and has been turned on.

Use TCP/IP to control the robotic arm

### 1. Client

```python
# demo
from pymycobot import MyCobot280Socket
# Port 9000 is used by default
mc = MyCobot280Socket("192.168.10.10",9000)

res = mc.get_angles()
print(res)

mc.send_angles([0,0,0,0,0,0],20)
...
```

### 2. Server

For details, please refer to the [TCP/IP](7_TCPIP.md) section.