# Demonstration code 

The following are various use cases and operation result videos. You can copy the code for use or modification (the robot arm model used in the following cases is MyCobot280 280. The parameters of different series of robot arms are different. Please pay attention to the modification).

**Note: ** The corresponding baud rates of various devices are different. Please refer to the information to understand their baud rates when using them. The serial port number can be viewed through [Calculator Device Manager](https://docs.elephantrobotics.com/docs/gitbook/4-BasicApplication/4.1-myStudio/4.1.1-myStudio_download_driverinstalled.html#4113-%E5%A6%82%E4%BD%95%E5%8C%BA%E5%88%86cp210x%E5%92%8Ccp34x%E8%8A%AF%E7%89%87) or the serial port assistant.

## 1 Control RGB light board

```python
from pymycobot import MyCobot280
import time
#The above needs to be written at the beginning of the code, which means importing the project package

# MyCobot280 class initialization requires two parameters: serial port and baud rate
    # The first is the serial port string, such as:
        # linux: "/dev/ttyUSB0"
        # windows: "COM3"
        # The second is the baud rate:
        # M5 version: 115200
    # The following is such as:
        # mycobot-M5:
            # linux:
            # mc = MyCobot280("/dev/ttyUSB0", 115200)
            # windows:
            # mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# The following is the object code for the Windows version
mc = MyCobot280("COM3", 115200)

i = 7
# Loop 7 times
while i > 0:
mc.set_color(0,0,255) #Blue light on
time.sleep(2) #Wait 2 seconds
mc.set_color(255,0,0) #Red light on
time.sleep(2) #Wait 2 seconds
mc.set_color(0,255,0) #Green light on
time.sleep(2) #Wait 2 seconds
i -= 1
```

## 2 Control the machine to return to the origin

```python
from pymycobot import MyCobot280
# MyCobot280 class initialization requires two parameters:
# The first is the serial port string, such as:
        # linux: "/dev/ttyUSB0"
        # windows: "COM3"
        # The second is the baud rate:
        # M5 version: 115200
    # The following is such as:
        # mycobot-M5:
            # linux:
            # mc = MyCobot280("/dev/ttyUSB0", 115200)
            # windows:
            # mc = MyCobot280("COM3", 115200)


# Initialize a MyCobot280 object
# The following is the object code for M5 version
mc = MyCobot280("COM3", 115200)

# Check if the robot can be programmed

if mc.is_controller_connected() != 1:

print("Please connect the robot correctly to write the program")

exit(0)

# Fine-tune the robot to ensure that all the ports are aligned

# The alignment of the robot port is the standard. This is just an example

mc.send_angles([0, 0, 0, 0, 0, 0], 30)

# Calibrate the position at this time. The calibrated angle position is [0,0,0,0,0,0] and the potential value is [2048,2048,2048,2048,2048,2048]

# This for loop is equivalent to the set_gripper_ini() method

#for i in range(1, 7):

#mc.set_servo_calibration(i)
```

## 3 Single joint movement

```python
from pymycobot import MyCobot280
import time

# The MyCobot280 class requires two parameters to be initialized:
# The first is the serial port string, such as:
        # linux: "/dev/ttyUSB0"
        # windows: "COM3"
        # The second is the baud rate:
        # M5 version: 115200
    # The following is such as:
        # mycobot-M5:
            # linux:
            # mc = MyCobot280("/dev/ttyUSB0", 115200)
            # windows:
            # mc = MyCobot280("COM3", 115200)

# Create object code for M5 version
mc=MyCobot280('COM3',115200)

# Robot arm recovery
mc.send_angles([0, 0, 0, 0, 0, 0], 40)
time.sleep(3)

# Control joint 3 to move 70°
mc.send_angle(Angle.J3.value,70,40)
time.sleep(3)

# Control joint 4 to move -70°
mc.send_angle(Angle.J4.value,-70,40)
time.sleep(3)

# Control joint 1 to move 90°
mc.send_angle(Angle.J1.value,90,40)
time.sleep(3)

# Control joint 5 to move -90°
mc.send_angle(Angle.J5.value,-90,40)
time.sleep(3)

# Control joint 5 to move 90°
mc.send_angle(Angle.J5.value,90,40)
time.sleep(3)
```



## 4 Multi-joint exercise

```python
import time
from pymycobot import MyCobot280
# The MyCobot280 class requires two parameters to be initialized:
#   The first is the serial port string, such as:
#       linux: "/dev/ttyUSB0"
#       windows: "COM3"
#   The second is the baud rate:
#       M5 version: 115200
#
#   Example:
#       mycobot-M5:
#           linux:
#                mc = MyCobot280("/dev/ttyUSB0", 115200)
#           windows:
#              mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# 280-M5 version object code
mc=MyCobot280('COM3',115200)
# Robot arm reset to zero
mc.send_angles([0,0,0,0,0,0],50)
time.sleep(2.5)
# Control the different angles of rotation of multiple joints
mc.send_angles([90,45,-90,90,-90,90],50)
time.sleep(2.5)
# Robot arm reset to zero
mc.send_angles([0,0,0,0,0,0],50)
time.sleep(2.5)
# Control the different angles of rotation of multiple joints
mc.send_angles([-90,-45,90,-90,90,-90],50)
time.sleep(2.5)

```

##  5 Control the robot arm to swing left and right

```python
from pymycobot import MyCobot280
import time

# M5 version
mc = MyCobot280("COM3", 115200)
# Get the coordinates of the current position
angle_datas = mc.get_angles()
print(angle_datas)

# Use a sequence to pass coordinate parameters to move the robot to the specified position
mc.send_angles([0, 0, 0, 0, 0, 0], 50)
print(mc.is_paused())
# Set the waiting time to ensure that the robot has reached the specified position
# while not mc.is_paused():
time.sleep(2.5)

# Move joint 1 to position 90
mc.send_angle(Angle.J1.value, 90, 50)

# Set the waiting time to ensure that the robot has reached the specified position
time.sleep(2)

# Set the number of loops
num = 5

# Let the robot swing left and right
while num > 0:
    # Move joint 2 to position 50
    mc.send_angle(2, 50, 50)
    # Set the waiting time to ensure that the robot has reached the specified position
    time.sleep(1.5)
    # Move joint 2 to position -50
    mc.send_angle(2, -50, 50)
    # Set the waiting time to ensure that the robot has reached the specified position
    time.sleep(1.5)
    num -= 1
# Retract the robot arm. You can swing the robot arm manually, and then use the get_angles() function to get the coordinate sequence.
# Use this function to make the robot arm reach the position you want.
mc.send_angles([88.68, -138.51, 155.65, -128.05, -9.93, -15.29], 50)

# Set the waiting time to ensure that the robot arm has reached the specified position
time.sleep(2.5)
# Relax the robot arm and swing it manually
mc.release_all_servos()

```

## 6 Controlling the robotic arm to dances

```python
from pymycobot import MyCobot280
import time

if __name__ == '__main__':
# MyCobot280 class initialization requires two parameters:
# The first is the serial port string, such as:
        # linux: "/dev/ttyUSB0"
        # windows: "COM3"
        # The second is the baud rate:
        # M5 version: 115200
    # The following is such as:
        # mycobot-M5:
            # linux:
            # mc = MyCobot280("/dev/ttyUSB0", 115200)
            # windows:
            # mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# M5 version
 mc = MyCobot280("COM3",115200)
# Set the start time
start = time.time()
# Let the robot reach the specified position
mc.send_angles([-1.49, 115, -153.45, 30, -33.42, 137.9], 80)
# Determine whether it has reached the specified position
while not mc.is_in_position([-1.49, 115, -153.45, 30, -33.42, 137.9], 0):
    # Let the robot resume movement
    mc.resume()
    # Let the robot move for 0.5s
    time.sleep(0.5)
    # Pause the movement of the robot
    mc.pause()
    # Determine whether the movement has timed out
    if time.time() - start > 3:
        break
# Set the start time
start = time.time()
# Let the movement last for 30 seconds
while time.time() - start < 30:
    # Let the robot reach this position quickly
    mc.send_angles([-1.49, 115, -153.45, 30, -33.42, 137.9], 80)
    # Set the color of the light to [0,0,50]
    mc.set_color(0, 0, 50)
    time.sleep(0.7)
    # Let the robot reach this position quickly
    mc.send_angles([-1.49, 55, -153.45, 80, 33.42, 137.9], 80)
    # Set the color of the light to [0,50,0]
    mc.set_color(0, 50, 0) 
    time.sleep(0.7)
```

## 7 Gripper control

```python
from pymycobot import MyCobot280
import time
def gripper_test(mc):
    print("Start check IO part of api\n")
    # Check if the gripper is moving
    flag = mc.is_gripper_moving()
    print("Is gripper moving: {}".format(flag))
    time.sleep(1)

    # Set the current position to (2048).
    # Use it when you are sure you need it.
    # Gripper has been initialized for a long time. Generally, there
    # is no need to change the method.
    # mc.set_gripper_ini()
    # Set joint point 1 to rotate to position 2048
    mc.set_encoder(1, 2048, 20)
    time.sleep(2)
    # Set six joint positions and let the robot arm rotate to the position at a speed of 20

    mc.set_encoders([1024, 1024, 1024, 1024, 1024, 1024], 20)
    # mc.set_encoders([2048, 2900, 2048, 2048, 2048, 2048], 20)
    # mc.set_encoders([2048, 3000,3000, 3000, 2048, 2048], 50)
    time.sleep(3)
    # Get the position information of joint point 1
    print(mc.get_encoder(1))
    # Set the gripper to rotate to the position of 2048
    mc.set_encoder(7, 2048, 20)
    time.sleep(3)
    # Set the gripper to rotate to the position of 1300
    mc.set_encoder(7, 1300, 20)
    time.sleep(3)

    # Let the gripper reach the state of 100 at a speed of 70
    mc.set_gripper_value(100, 70)
    time.sleep(3)
    # Let the gripper reach the state of 0 at a speed of 70
    mc.set_gripper_value(0, 70)
    time.sleep(3)

    num=5
    while num>0:
        # Set the state of the gripper to open the claws quickly at a speed of 70
        mc.set_gripper_state(0, 70)
        time.sleep(3)
        # Set the state of the gripper to close the claws quickly at a speed of 70
        mc.set_gripper_state(1, 70)
        time.sleep(3)
        num-=1

    # Get the value of the gripper
    print("")
    print(mc.get_gripper_value())
    # mc.release_all_servos()

if __name__ == "__main__":
# MyCobot280 class initialization requires two parameters:
#   The first is the serial port string, such as:
#       linux: "/dev/ttyUSB0"
#windows: "COM3"
#   The second is the baud rate:
#       M5 version is: 115200
#
#   Example:
#       mycobot-M5:
#           linux:
#              mc = MyCobot280("/dev/ttyUSB0", 115200)
#           windows:
#              mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# M5 version
mc = MyCobot280('COM3', 115200)
# Move it to zero position

mc.set_encoders([2048, 2048, 2048, 2048, 2048, 2048], 20)
time.sleep(3)
gripper_test(mc)
```

## 8 Suction pump control

280-M5

```python
from pymycobot import MyCobot280
import time

# The MyCobot280 class requires two parameters to initialize:
#   The first is the serial port string, such as:
#       linux: "/dev/ttyUSB0"
#       windows: "COM3"
#   The second is the baud rate:
#       M5 version: 115200
#
#   Example:
#       mycobot-M5:
#           linux:
#              mc = MyCobot280("/dev/ttyUSB0", 115200)
#           windows:
#              mc = MyCobot280("COM3", 115200)

# Initialize a MyCobot280 object
# The following is the object code for the M5 version
mc = MyCobot280('COM3',115200)
# The position of the robot arm movement
angles = [
[92.9, -10.1, -60, 5.8, -2.02, -37.7],
[92.9, -53.7, -83.05, 50.09, -0.43, -38.75],
[92.9, -10.1, -87.27, 5.8, -2.02, -37.7]
]

# Turn on the suction pump
def pump_on():
    # Open the solenoid valve
    mc.set_basic_output(5, 0)
    time.sleep(0.05)

# Stop the suction pump
def pump_off():
    # Close the solenoid valve
    mc.set_basic_output(5, 1)
    time.sleep(0.05)
    # The exhaust valve starts working
    mc.set_basic_output(2, 0)
    time.sleep(1)
    mc.set_basic_output(2, 1)
    time.sleep(0.05)

# Robot arm recovery
mc.send_angles([0, 0, 0, 0, 0, 0], 30)
time.sleep(3)

# Turn on the suction pump
pump_on()
mc.send_angles(angles[2], 30)
time.sleep(2)

# Suction small objects
mc.send_angles(angles[1], 30) 
time.sleep(2) 
mc.send_angles(angles[0], 30) 
time.sleep(2)
mc.send_angles(angles[1], 30)
time.sleep(2) 
#Turn off the suction pump 
pump_off() 
mc.send_angles(angles[0], 40) 
time.sleep(1.5)
```

