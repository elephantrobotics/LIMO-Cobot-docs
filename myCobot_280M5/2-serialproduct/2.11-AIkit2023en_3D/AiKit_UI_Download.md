# **AiKit 3D UI Instructions**

## 1 AiKit 3D UI Download

### **1.1** Use git to download the project

Enter the URL: https://github.com/elephantrobotics/AiKit_3D_UI/tree/main

- Use git clone, under the ‘Code’ button, take the first address as an example
  
   ![28](/resourse/13-AdvancedKit/AiKit_3D/3d-9.png)

- Right click in the folder to open the git window

![image-20230109101120225](/resourse/13-AdvancedKit/AiKit_UI_img/29.png)

- Depending on the model and device, enter the command:

  - mechArm 270 M5

  ```bash
  cd Desktop
  # If you use the Obi medium-light Deeyea camera, execute this command
  git clone https://github.com/elephantrobotics/AiKit_3D_UI.git
  # If using RealSense camera, execute this command
  git clone -b realsense_UI https://github.com/elephantrobotics/AiKit_3D_UI.git
  ```

  - myCobot 280 M5

  ```bash
  cd Desktop
  # If you use the Obi medium-light Deeyea camera, execute this command
  git clone -b Deeyea_280_M5 https://github.com/elephantrobotics/AiKit_3D_UI.git
  # If using RealSense camera, execute this command
  git clone -b Realsense_280_M5 https://github.com/elephantrobotics/AiKit_3D_UI.git
  ```
 
## 2 start method

In PyCharm, under the path `/AiKit_3D_UI`:

- Terminal run
  
```python
python3 <path>/main.py
```

- You can directly run the `main.py` script in the `/AiKit_3D_UI` path in PyCharm

After the startup is successful, as shown in the figure below:<br>

![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-1.png) 

## 3 Features

##### **language switch**

Click the button in the upper right corner of the window to switch between languages (Chinese, English).<br>
![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-2.png)

##### **device connection**

1. Select serial port, device, baud rate<br>![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-3.png)
2. Click the 'CONNECT' button to connect, after the connection is successful, the 'CONNECT' button will change to 'DISCONNECT'<br>
   ![img](/resourse/13-AdvancedKit/AiKit_UI_img/3.png)

3. Clicking the 'DISCONNECT' button will disconnect the robot arm<br>
   ![img](/resourse/13-AdvancedKit/AiKit_UI_img/4.png)

4. After the robotic arm is successfully connected, the gray button will be lit and become clickable.<br>
   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-4.png)

##### **Turn on the camera**

1. When the program runs successfully, turn on the camera.<br>
   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-5.png)

2. Click the 'Open' button to try to open the camera. If it fails to open, you should check whether the camera is connected correctly; the camera is successfully opened as shown in the figure below: Note: Before use, the camera should be adjusted to be parallel to the desktop.<br>
   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-6.png)

##### **algorithm control**


1. Go back to the initial point of grabbing, click the 'Go' button, it will stop the current operation and return to the initial point.<br>![img](/resourse/13-AdvancedKit/AiKit_UI_img/10.png)

2. Step-by-step 
   Recognition recognition: click the 'Run' button to start the recognition, Aigorithm is the current algorithm used. <br>
   ![img](/resourse/13-AdvancedKit/AiKit_UI_img/11.png)
   Pick: Click the 'Run' button to start the capture. After the capture is successful, the recognition and capture will be automatically closed, and you need to click it again for the next use. <br>
   ![img](/resourse/13-AdvancedKit/AiKit_UI_img/12.png)

3. Placement: Click the "Run" button to start placement. The BinA, BinB, BinC, and BinD selection boxes correspond to the four storage boxes of BinA, BinB, BinC, and BinD respectively. After selection, they will be placed in the specified storage box.<br>

   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-7.0.png)

4. Grasping point adjustment, X offset, Y offset, and Z offset respectively represent the position of the X-axis, Y-axis, and Z-axis of the robot arm coordinates, and can be modified according to actual needs.

   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-7.1.png)


5. Algorithm selection includes **Color Recognition Suction Pump**, **Shape Recognition Suction Pump**, **yolov8 Suction Pump**, **Depalletizing Suction Pump**, **Color Recognition Clamp**, **yolov8 gripper**, selecting the corresponding algorithm will perform corresponding recognition.<br>

   ![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-7.png)


##### **coordinate display**

1. Real-time coordinate display of the robotic arm: click the 'current coordinates' button to open<br>![img](/resourse/13-AdvancedKit/AiKit_3D/可视化-8.png)

2. Recognition coordinate display: click the ''image coordinates' button to open<br>
   ![image-20230106180304086](/resourse/13-AdvancedKit/AiKit_3D/可视化-9.png)

## 4 Usage steps

The **numbering sequence** in the figure is the order of steps.

![image-20230106180304086](/resourse/13-AdvancedKit/AiKit_3D/使用步骤-1.png)

- When switching algorithms, if you switch from the gripper algorithm to the suction pump algorithm or from the suction pump algorithm to the gripper algorithm, you must perform **Step 3** because some parameter configurations of the gripper or suction pump need to be initialized. .

- After **Step 3** is completed, the button color will change back to blue

- When performing the depalletizing algorithm, the grabbing process only needs to go through **Step 6**, and there is no need to go through **Step 7**,**and it will not be recognized during the grabbing process, but the grabbing process operation is completed once After that, it will continue to identify and crawl, and so on**

- Only after executing **Step 3** can you view the image coordinates. If the image coordinates are all 0, it means that they have not been recognized.

- The current coordinates can only be viewed after executing **Step 1**.

- The xyz offset can be modified and saved before executing **Step 6**. It can be modified according to the actual crawling situation. It is not modified by default. Taking the front of the robotic arm as the benchmark, the larger the x value, the farther forward the end is to grab, and vice versa; the larger the y value, the further the end is to grab, and vice versa. **Fetch to the right**; the larger the z value, the further **up** you will grab, and vice versa.

## 5 Precautions

1. The M5 version model uses serial port baud rate connection.

2. After selecting the algorithm and modifying the offset, the recognition program can be started.

3. After the recognition program is started successfully, you can click the camera button to view the camera screen information.

4. Only after crawling can you view the coordinate display information.

5. If you need to switch algorithms during use, stop the current recognition program first, and then switch algorithms.
