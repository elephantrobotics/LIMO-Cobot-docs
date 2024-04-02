# MyBuddy Python API
### base_to_single_coords(base_coords, arm)

Convert base coordinates to coordinates

- **Parameters**

  - **coords** – a list of base coords value len 6

  - **arm** – 0 - left. 1 - right

- **Returns**

    coords

### collision(left_angles, right_angles)

Collision detection main program

- **Parameters**

  - **left_angles** – left arm angle len 6.

  - **right_angles** – right arm angle len 6.

- **Returns**

    int

### collision_switch(state)

Collision Detection Switch

- **Parameters**

    **state** (_int_) – 0 - close 1 - open (Off by default)

### focus_servo(id, servo_id)

Power on designated servo

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_id** – 1 - 6

### get_acceleration(id)

Read acceleration during all moves

- **Parameters**

    **id** – 1/2/3 (L/R/W)

### get_angle(id, joint_id)

Get the angle of a single joint

- **Parameters**

  - **id** (_int_) – 1/2/3 (L/R/W).

  - **joint_id** (_int_) – 1 - 7 (7 is gripper)

### get_angles(id)

Get the degree of all joints.

- **Parameters**

    **id** – 1/2 (L/R)

- **Returns**

    A float list of all degree.

- **Return type**

    list

### get_base_coord(id)

Get the base coordinates of the single arm

- **Parameters**

    **id** – 1/2 (L/R)

### get_base_coords(\*args: int)

Convert coordinates to base coordinates. Pass in parameters or no parameters

- **Parameters**

  - **coords** – a list of coords value(List[float]), length 6 [x(mm), y, z, rx(angle), ry, rz]

  - **arm** – 0 - left. 1 - right

- **Returns**

    Base coords

### get_coord(id, joint_id)

Read a single coordinate parameter

- **Parameters**

  - **id** (_int_) – 1/2/3 (L/R/W).

  - **joint_id** (_int_) – 1 - 7 (7 is gripper)

### get_coords(id)

Get the coordinates of the robotic arm

- **Parameters**

    **id** – 1/2 (L/R).

### get_digital_input(id, pin_no)

singal value

- **Parameters**

  - **id** – 1/2 (L/R)

  - **pin_no** (_int_) – 1 - 5

### get_encoder(id, joint_id)

Obtain the specified joint potential value.

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – (int) 1 ~ 6

- **Returns**

    0 ~ 4096

### get_encoders(id)

Get the six joints of the manipulator

- **Parameters**

    **id** – 1/2 (L/R).

- **Returns**

    The list of encoders

### get_end_type(id)

Get end coordinate system

- **Parameters**

    **id** – 0/1/2 (ALL/L/R)

- **Returns**

    0 - flange
    1 - tool

### get_gripper_value(id)

Get the value of gripper.

- **Parameters**

    **id** – 1/2 (L/R)

- **Returns**

    gripper value (int)

### get_joint_current(id, joint_id)

Get Collision Current

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **joint_id** – 1 - 6

### get_joint_max_angle(id, joint_id)

Gets the maximum movement angle of the specified joint

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint_id** – (int) 1 - 6

- **Returns**

    angle value(float)

### get_joint_min_angle(id, joint_id)

Gets the minimum movement angle of the specified joint

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint_id** – (int) 1 - 6

- **Returns**

    angle value(float)

### get_movement_type(id)

Get movement type

- **Parameters**

    **id** – 0/1/2 (ALL/L/R)

- **Returns**

    1 - movel
    0 - moveJ

### get_plan_acceleration(id=0)

Get planning acceleration

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

- **Returns**

    [movel planning acceleration, movej planning acceleration].

### get_plan_speed(id=0)

Get planning speed

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

- **Returns**

    [movel planning speed, movej planning speed].

### get_reference_frame(id)

Get the base coordinate system

- **Parameters**

    **id** – 0/1/2 (ALL/L/R)

- **Returns**

    0 - base 1 - tool.

### get_robot_id(id)

Detect this robot id

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### get_robot_version(id)

Get cobot version

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### get_servo_currents(id)

Get joint current

- **Parameters**

    **id** – 1/2/3 (L/R/W)

- **Returns**

    value mA

### get_servo_data(id, servo_no, data_id)

Read the data parameter of the specified address of the steering gear.

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_no** – Serial number of articulated steering gear, 1 - 6.

  - **data_id** – Data address.

- **Returns**

    values (0 - 4096)
    0 - disable
    1 - enable
    -1 - error

### get_servo_status(id)

Get joint status

- **Parameters**

    **id** – 1/2/3 (L/R/W)

- **Returns**

    [voltage, sensor, temperature, current, angle, overload], a value of 0 means no error

### get_servo_temps(id)

Get joint temperature

- **Parameters**

    **id** – 1/2/3 (L/R/W)

### get_servo_voltages(id)

Get joint voltages

- **Parameters**

    **id** – 1/2/3 (L/R/W)

- **Returns**

    volts < 24 V

### get_speed(id)

Get speed

- **Parameters**

    **id** – 1/2/3 (L/R/W).

- **Returns**

    speed

- **Return type**

    int

### get_system_version(id)

Get cobot version

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### get_tool_reference(id)

Get tool coordinate system

- **Parameters**

    **id** – 0/1/2 (ALL/L/R)

### get_world_reference(id)

Get the world coordinate system

- **Parameters**

    **id** – 0/1/2 (ALL/L/R)

### is_all_servo_enable(id)

Determine whether the specified steering gear is connected

- **Parameters**

    **id** – 1/2/3 (L/R/W)

- **Returns**

    0 - disable
    1 - enable
    -1 - error

### is_collision_on()

Get collision detection status

### is_controller_connected(id=0)

Wether connected with Atom.

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### is_free_mode(id)

Check if it is free mode

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

- **Returns**

    0/1

### is_gripper_moving(id)

Judge whether the gripper is moving or not

- **Parameters**

    **id** – 1/2 (L/R)

- **Returns**

    0 - not moving
    1 - is moving
    -1 - error data

### is_in_position(id, data, mode)

Judge whether in the position.

- **Parameters**

  - **id** – 0/1/2/3 (ALL/L/R/W).

  - **data** – A data list, angles or coords. If id is 1/2. data length is 6. If id is 0. data len 13. if id is 3. data len 1

  - **mode** – 1 - coords, 0 - angles

- **Returns**

    1 - True
    0 - False
    -1 - Error

### is_moving(id)

Detect if the robot is moving

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W).

- **Returns**

    0 - not moving
    1 - is moving
    -1 - error data

### is_paused(id)

Judge whether the manipulator pauses or not.

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W).

- **Returns**

    1 - paused
    0 - not paused
    -1 - error

### is_power_on(id=0)

Adjust robot arm status

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

- **Returns**

    1 - power on
    0 - power off
    -1 - error data

### is_servo_enable(id, servo_id)

Determine whether all steering gears are connected

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_id** – (int) 1 ~ 6

- **Returns**

    0 - disable
    1 - enable
    -1 - error

### jog_absolute(id, joint_id, angle, speed)

Absolute joint control

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – int 1-6.

  - **angle** – int

  - **speed** – int (0 - 100)

### jog_angle(id, joint_id, direction, speed)

Jog control angle.

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – int 1-6.

  - **direction** – 0 - decrease, 1 - increase

  - **speed** – int (0 - 100)

### jog_coord(id, coord_id, direction, speed)

Jog control coord.

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **coord_id** – int 1-6 (x/y/z/rx/ry/rz).

  - **direction** – 0 - decrease, 1 - increase

  - **speed** – int (0 - 100)

### jog_inc_coord(axis, increment, speed)

Double-arm coordinated coordinate stepping

- **Parameters**

  - **axis** – 1 - 6 (x/y/z/rx/ry/rz)

  - **increment** –

  - **speed** – 1 - 100

### jog_increment(id, joint_id, increment, speed)

step mode

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – int 1-6.

  - **increment** –

  - **speed** – int (1 - 100)

### jog_stop(id)

Stop jog moving

- **Parameters**

    **id** – 1/2/3 (L/R/W).

### joint_brake(id, joint_id)

Make it stop when the joint is in motion, and the buffer distance is positively related to the existing speed

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint_id** – 1 - 6

### pause(id)

Pause movement

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W).

### power_off(id=0)

Close communication with Atom.

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### power_on(id=0)

Open communication with Atom.

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### read_next_error(id=0)

Robot Error Detection

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### release_all_servos(id=0)

Robot turns off torque output

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W)

### release_servo(id, servo_id)

Power off designated servo

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_id** – 1 - 6.

### resume(id)

Recovery movement

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W).

### send_angle(id, joint, angle, speed)

Send one degree of joint to robot arm.

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint** – 1 ~ 6

  - **angle** – int

  - **speed** – 1 ~ 100

- **Returns**
  - None

### send_angles(id, degrees, speed)

Send all angles to the robotic arm

- **Parameters**

  - **id** – 1/2 (L/R).

  - **degrees** – [angle_list] len 6

  - **speed** – 1 - 100

### send_coord(id, coord, data, speed)

Send a single coordinate to the robotic arm

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **coord** – 1 ~ 6 (x/y/z/rx/ry/rz)

  - **data** – int

  - **speed** – 0 ~ 100

### send_coords(id, coords, speed, mode)

Send all coords to robot arm.

- **Parameters**

  - **id** – 1/2 (L/R).

  - **coords** – a list of coords value(List[float]), length 6, [x(mm), y, z, rx(angle), ry, rz]

  - **speed** – (int) 0 ~ 100

  - **mode** – (int) 0 - moveJ, 1 - moveL, 2 - moveC

### set_acceleration(id, acc)

Read acceleration during all moves

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **acc** – 1 - 100

### set_color(id, r=0, g=0, b=0)

Set the light color on the top of the robot arm.

- **Parameters**

  - **id** – 1/2 (L/R)

  - **r** (_int_) – 0 ~ 255

  - **g** (_int_) – 0 ~ 255

  - **b** (_int_) – 0 ~ 255

### set_digital_output(id, pin_no, pin_signal)

Set atom IO output level

- **Parameters**

  - **id** – 1/2 (L/R)

  - **pin_no** (_int_) – 1 - 5

  - **pin_signal** (_int_) – 0 / 1

### set_encoder(id, joint_id, encoder, speed)

Set a single joint rotation to the specified potential value.

- **Parameters**

  - **id** – 1/2/3 (L/R/W).

  - **joint_id** – 1 - 6.

  - **encoder** – The value of the set encoder.

### set_encoders(id, encoders, speed)

Set the six joints of the manipulator to execute synchronously to the specified position.

- **Parameters**

  - **id** – 1/2 (L/R).

  - **encoders** – A encoder list, length 6.

  - **speed** – speed 1 ~ 100

### set_end_type(id, end)

Set end coordinate system

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **end** – 0 - flange, 1 - tool

### set_free_mode(id, value)

set free mode

- **Parameters**

  - **id** – 0/1/2/3 (ALL/L/R/W)

  - **value** – 0 - close 1 - open

### set_fresh_mode(id, mode)

Set command refresh mode

- **Parameters**

  - **id** – 1/2 (L/R).

  - **mode** – int
    0 - Always execute the latest command first.
    1 - Execute instructions sequentially in the form of a queue.

### set_gripper_calibration(id)

Set the current position to zero, set current position value is 2048.

- **Parameters**

    **id** – 1/2 (L/R)

### set_gripper_state(id, flag)

Set gripper switch state

- **Parameters**

  - **id** – 1/2 (L/R)

  - **flag** (_int_) – 0 - close, 1 - open

### set_gripper_value(id, value, speed)

Set gripper value

* **Parameters**

  * **id** – 1/2 (L/R)

  * **value** (_int_) – 0 ~ 100

  * **speed** (_int_) – 0 ~ 100

### set_joint_current(id, joint_id, current)

Set Collision Current

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **joint_id** – 1 - 6

  - **current** – current value

### set_joint_max(id, joint_id, angle)

Set the joint maximum angle

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint_id** – int 1-6.

  - **angle** – 0 ~ 180

### set_joint_min(id, joint_id, angle)

Set the joint minimum angle

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **joint_id** – int 1-6.

  - **angle** – 0 ~ 180

### set_movement_type(id, move_type)

Set movement type

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **move_type** – 1 - movel, 0 - moveJ

### set_pin_mode(id, pin_no, pin_mode)

Set the state mode of the specified pin in atom.

- **Parameters**

  - **id** – 1/2 (L/R)

  - **pin_no** (_int_) – pin number (1 - 5).

  - **pin_mode** (_int_) – 0 - input, 1 - output

### set_plan_acceleration(id, acceleration)

Set planning acceleration

- **Parameters**

  - **id** – 0/1/2/3 (ALL/L/R/W)

  - **acceleration** (_int_) – (0 ~ 100).

### set_plan_speed(id, speed)

Set planning speed

- **Parameters**

  - **id** – 0/1/2/3 (ALL/L/R/W)

  - **speed** (_int_) – (0 ~ 100).

### set_pwm_output(id, channel, frequency, pin_val)

PWM control

- **Parameters**

  - **id** – 1/2 (L/R)

  - **channel** (_int_) – IO number (1 - 5).

  - **frequency** (_int_) – clock frequency (0/1: 0 - 1Mhz 1 - 10Mhz)

  - **pin_val** (_int_) – Duty cycle 0 ~ 100: 0 ~ 100%

### set_reference_frame(id, rftype)

Set the base coordinate system

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **rftype** – 0 - base 1 - tool.

### set_robot_id(id, new_id)

Set this robot id

- **Parameters**

  - **id** – 0/1/2/3 (ALL/L/R/W)

  - **new_id** – 1 - 253

### set_servo_calibration(id, servo_no)

The current position of the calibration joint actuator is the angle zero point,

    and the corresponding potential value is 2048.

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_no** – Serial number of articulated steering gear, 1 - 6.

### set_servo_data(id, servo_no, data_id, value)

Set the data parameters of the specified address of the steering gear

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **servo_no** – Serial number of articulated steering gear, 1 - 6.

  - **data_id** – Data address.

  - **value** – 0 - 4096

### set_speed(id, speed)

Set speed value

- **Parameters**

  - **id** – 1/2/3 (L/R/W)

  - **speed** (_int_) – 0 - 100

### set_tool_reference(id, coords)

Set tool coordinate system

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **coords** – a list of coords value(List[float]), length 6. [x(mm), y, z, rx(angle), ry, rz]

### set_world_reference(id, coords)

Set the world coordinate system

- **Parameters**

  - **id** – 0/1/2 (ALL/L/R)

  - **coords** – a list of coords value(List[float]), length 6 [x(mm), y, z, rx(angle), ry, rz]

### stop(id)

Stop moving

- **Parameters**

    **id** – 0/1/2/3 (ALL/L/R/W).

### write_base_coord(id, axis, coord, speed)

Base single coordinate movement

- **Parameters**

  - **id** – 1/2 (L/R)

  - **axis** – 1 - 6 (x/y/z/rx/ry/rz)

  - **coord** – Coordinate value

  - **speed** – 1 - 100

### write_base_coords(id, coords, speed)

base coordinate move

- **Parameters**

  - **id** – 1/2 (L/R)

  - **coords** – coords: a list of coords value(List[float]), length 6, [x(mm), y, z, rx(angle), ry, rz]

  - **speed** – 1 - 100

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

- **Parameters**

  - **id** – 1/2 (L/R).

  - **radians** – a list of radian values( List[float]), length 6

  - **speed** – (int )0 ~ 100

### set_gpio_input(pin)

Set GPIO input value.

- **Parameters**

    **pin** – (int)pin number.

### set_gpio_mode(pin_no, mode)

Init GPIO module, and set BCM mode.

- **Parameters**

  - **pin_no** – (int)pin number.

  - **mode** – 0 - input 1 - output

### set_gpio_output(pin, v)

Set GPIO output value.

- **Parameters**

  - **pin** – (int)pin number.

  - **v** – (int) 0 / 1

### set_gpio_pwm(pin, baud, dc)

Set GPIO PWM value.

- **Parameters**

  - **pin** – (int)pin number.

  - **baud** – (int) 10 - 1000000

  - **dc** – (int) 0 - 100
