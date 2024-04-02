# Use Cases

This use case employs the eye-to-hand mode using a 3D camera, combining **Python** with **OpenCV**. It utilizes OpenCV for color, shape, and YOLOv5 object detection to identify and box appropriate objects. The spatial coordinates of the objects relative to the robotic arm are then calculated based on relevant points. A set of related actions is defined for the robotic arm to place the objects in different areas based on their recognition.

**Supported End Effectors:** myCobot Vertical Vacuum Pump V2.0, myCobot Adaptive Gripper

**Supported cameras:** Obi Zhongguang Deeyea camera, RealSense camera

**Case summary**

- Gripper: color recognition, YOLO recognition
- Suction pump: color recognition, shape recognition, YOLO recognition, depalletizing

### **1 Recognition Case**

Depending on the end effector, different script files are run.

#### **1.1 Suction pump**

In PyCharm, under the path `/AiKit_3D_UI/demos/pump_demos`

- If color recognition is performed, run the script file `pump_color_demo.py`.
- If performing shape recognition, run the script file `pump_shape_demo.py`.
- If YOLO recognition is performed, run the script file `pump_yolo_demo.py`.
- If the depalletizing program is performed, run the script file `pump_depalleting_demo.py`.

#### **1.2 Gripper**

In PyCharm, under the path `/AiKit_3D_UI/demos/gripper_demos`

- If color recognition is performed, run the script file `gripper_color_demo.py`.
- If YOLO recognition is performed, run the script file `gripper_yolo_demo.py`.

**Precautions**

1. The program needs to be run in a virtual environment.

2. If the point capture is not accurate, you can modify the value of `(x,y,z)` in the corresponding script file. Based on the front of the machine, the larger the x value, the further forward the end will be. Grab, on the contrary, the farther the y value is, the farther the end is to the left, and vice versa; the larger the z value, the farther the end is to grab. Go up to grab, otherwise go down to grab. It can be adjusted according to the actual situation.
   
3. If the 3D camera image is dim or too bright, if using a Deeyea camera, open the OpenNI2 Viewer tool, turn off the `exposure mode`, and manually set the exposure control value. If using a RealSense camera, open the Intel.RealSense.Viewer.exe tool and set the exposure control value under the RGB model.
   
4. OpenCV image recognition will be affected by the environment. If it is in a darker environment, the recognition effect will be greatly reduced.