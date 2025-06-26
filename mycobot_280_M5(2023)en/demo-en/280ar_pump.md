# Robot suction pump to carry wooden blocks

## 1 Functional description
The robot will use the suction pump to carry wooden blocks from point A to point B

## 2 Hardware installation
Insert the Lego connector into the reserved socket on the suction pump

![](./img/y0.jpg)

Align the suction pump with the connector inserted into the socket at the end of the robotic arm

![](./img/y1.jpg)

Select the male-female DuPont wire, and insert the female end into the socket marked with pins on the suction pump box

![](./img/p2.jpg)

![](./img/p3.jpg)

Then connect the wire to the end IO of the robotic arm

![](./img/AR.jpg)
> The left side is the suction pump pin, and the right side is the robotic arm pin
> GND -> GND
> 5V -> 5V
> G2 -> 23
> G5 -> 33

## 3 Pump test
Run the following program, the pump will repeat the opening and closing action twice
```python
from pymycobot import MyCobot280,utils
import time

arm = MyCobot280(utils.get_port_list()[0])
time.sleep(2)
# Turn on the pump
def pump_on():
    arm.set_digital_output(33, 0)
    time.sleep(0.05)

# Stop the pump
def pump_off():
    arm.set_digital_output(33, 1)
    time.sleep(0.05)
    arm.set_digital_output(23, 0)
    time.sleep(1)
    arm.set_digital_output(23, 1)
    time.sleep(0.05)

for i in range(2):
    pump_on()
    time.sleep(2)
    pump_off()
    time.sleep(2)
```

## 4 Software Usage
Use the fast movement function of myblockly to teach the grab and place points of the wooden block, and record the position information. After teaching, you need to disconnect the serial port, otherwise the serial port will be reported when running the python script.
![](./img/blockly.png)

## 5 Composite Application
```python
from pymycobot import MyCobot280,utils
import time
init_angles=[33.22, -15.55, -100.54, 25.48, 6.76, -13.35]#6 joint angles at the initial position
grab_point=[189.9, 12.1, 54.5, -178.15, 6.89, -43.47]#Coordinates of the grab point
place_point=[189.9, 120.1, 62.5, -178.15, 6.89, -43.47]# Coordinates of the placement point

arm = MyCobot280(utils.get_port_list()[0])
time.sleep(2)
# Turn on the suction pump
def pump_on():
    arm.set_digital_output(33, 0)
    time.sleep(0.05)

# Stop the suction pump
def pump_off():
    arm.set_digital_output(33, 1)
    time.sleep(0.05)
    arm.set_digital_output(23, 0)
    time.sleep(1)
    arm.set_digital_output(23, 1)
    time.sleep(0.05)

if __name__=="__main__":
    pump_off()#Turn off the suction pump first
    time.sleep(1)
    arm.send_angles(init_angles,100)#Move to the initial position
    time.sleep(2)
    arm.send_coords([grab_point[0],grab_point[1],grab_point[2]+70,grab_point[3],grab_point[4],grab_point[5]],100,1)#Move to 70mm above the grab point
    time.sleep(2)
    arm.send_coords([grab_point[0],grab_point[1],grab_point[2],grab_point[3],grab_point[4],grab_point[5]],100,1)#Move to the grab point
    time.sleep(2)
    pump_on() #Turn on the suction pump
    time.sleep(1)
    arm.send_coords([grab_point[0],grab_point[1],grab_point[2]+70,grab_point[3],grab_point[4],grab_point[5]],100,1)#Move to 70mm above the grab point
    time.sleep(2)
    
    arm.send_coords([place_point[0],place_point[1],place_point[2]+70,place_point[3],place_point[4],place_point[5]],100,1)#Move to 70mm above the placement point
    time.sleep(2)
    arm.send_coords([place_point[0],place_point[1],place_point[2],place_point[3],place_point[4],place_point[5]],100,1)#Move to the placement point
    time.sleep(2)
    pump_off() #Turn off the pump
    time.sleep(1)
    arm.send_coords([place_point[0],place_point[1],place_point[2]+70,place_point[3],place_point[4],place_point[5]],100,1)#Move to 70mm above the placement point
    time.sleep(2)

```
## 6 Effect display
![](./img/arduino_pump.gif)