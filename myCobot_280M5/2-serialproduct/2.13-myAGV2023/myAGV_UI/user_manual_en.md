
# myAgv software user manual

## Running Programme
1、Clone the github's repository：` https://github.com/elephantrobotics/AGV_UI.git`  
2、Switch to the branch **Visualize_OP** : `git checkout Visualize_OP`  
3、Install all dependences：
`
pip install -r requirements.txt 
`  
4、Running the command in the termial：
`
python operations.py  
`

![Softeware Page](../../../resourse/20-myAgv2023/AGV_UI/software_page_en.png "Software Page")

## 1、 Language Switch

Select Chinese and English to switch the corresponding language.

![Language Choose](../../../resourse/20-myAgv2023/AGV_UI/language_choices_en.png "Choose Language")

## 2、 Laser Radar

![Radar Open](../../../resourse/20-myAgv2023/AGV_UI/radar_open_en.png "Open Radar")

![Radar Close](../../../resourse/20-myAgv2023/AGV_UI/radar_close_en.png "Close Radar")


* Click the button to open the radar. The button turns red and the text display "Off".
* myAgv’s radar starts to rotate.
* A new terminal appears on the desktop, indicating that the radar is successfully opened.  
   ![Radar Open](../../../resourse/20-myAgv2023/AGV_UI/radar_open_terminal.png "Open Radar")

**Limit:**  

* Radar On: basic control, mapping, navigation, and map saving functions can be used.
* Radar Off:
  * LED light control and test functions can be used 
  * Before turning off the radar, you need to ensure that the basic control, mapping, and navigation functions have been turned off.

## 3、 Basic Control

>There are two ways to control the machine move by keyboard and handle.

![Basic Control](../../../resourse/20-myAgv2023/AGV_UI/basic_control_en.png "Basic Control")

**Predictions：** The radar needs to be turned on before turning on the basic control. If it is not turned on, a prompt box will pop up showing "Radar is not turned on".

Click the drop-down box to select the required control method, and click the button on the left to open. At this time, a new terminal will open on the desktop.

### 3.1 Keyboard Control

   ![Keyboard terminal](../../../resourse/20-myAgv2023/AGV_UI/keyboard_terminal.png "Keyboard terminal")  

**Directional keys:**

Keystrokes    | Directions
-------- | -----
i  | forward
，  | Backward
j | Move left
l | Move right
u|Rotate counterclockwise
o|clockwise rotation
k|stop

### 3.2 Handle Control

#### 2.1 Handle-Letter type

   ![JoyStick Alphabet](../../../resourse/20-myAgv2023/AGV_UI/joystick_terminal.jpg  "JoyStick Alphabet")

   >There are 7 buttons on the handle to control the car movement, as shown in the picture, 1~4 control the car forward and backward and left and right movement, 5 control the car counterclockwise rotation, 6 control the car clockwise rotation, 7 is the stop button.

   ![JoyStick Alphabet](../../../resourse/20-myAgv2023/AGV_UI/joystick_alphabet.jpg)

---

#### 2.2 Handle-Digital type


   ![JoyStick Number](../../../resourse/20-myAgv2023/AGV_UI/joystick_terminal.jpg "JoyStick Number")

   >There are 7 buttons on the handle to control the car movement, as shown in the picture, 1~4 control the car forward and backward and left and right movement, 5 control the car counterclockwise rotation, 6 control the car clockwise rotation, 7 is the stop button.


   ![JoyStick Number](../../../resourse/20-myAgv2023/AGV_UI/joystick_number.png "JoyStick Number")

## 4. Map and Navigation


![Map Navigation](../../../resourse/20-myAgv2023/AGV_UI/map_navi_en.png "Map and navigation")

**Preconditions：**

* Open radar
* Open keyboard control  

If it is not opened, a prompt box will pop up to prompt for the items that need to be opened.

### 4.1 Build Map

**There are two way for building map by Gmapping and Cartographer.**


![Build Map](../../../resourse/20-myAgv2023/AGV_UI/build_map_en.png  "Build Map")

#### Gmapping

Click the drop-down box to select the Gmapping mapping method, and click the "Open Mapping" button to start mapping.

* Desktop display rviz interface.
* Select the opened keyboard terminal and use the keyboard to control the car. The rviz space will build the map as the car moves. The trajectory is shown in the figure:  ![Gmapping Map](../../../resourse/20-myAgv2023/AGV_UI/gmapping_rviz.png  "Gmapping Map")

#### Cartographer

Click the drop-down box to select the Gmapping mapping method, and click the "Open Mapping" button to start mapping.

* Click the button and it will open a new terminal. If the terminal keeps scrolling the output data, the cartographer build file is successfully opened, and the terminal displays the following status:  ![Cartographer Map](../../../resourse/20-myAgv2023/AGV_UI/cartographer_terminal.png)
* When the code runs successfully, rviz will be opened, and the map and lidar information will be displayed in rviz, and the red arrow is the direction of the car. The interface is shown in the figure.   ![Cartographer Map](../../../resourse/20-myAgv2023/AGV_UI/cartograph_rviz.jpg)
* Select the opened keyboard terminal and use the keyboard to control the car. The rviz space will build the map as the car moves. The trajectory is shown in the figure:  ![Cartographer Track](../../../resourse/20-myAgv2023/AGV_UI/catograph_rviz2.jpg)

**Limit:** Navigation cannot be used after mapping is turned on; if you need to use the navigation function, please turn off mapping first.

#### 4.1.1 Save Map

![Save Map](../../../resourse/20-myAgv2023/AGV_UI/save_map_en.png "Save Map")


Click the "Save Map" button, and a new terminal will appear on the desktop to display the saved map information, as shown in the figure. The red circled part in the picture is the saved map file:


![Save map terminal](../../../resourse/20-myAgv2023/AGV_UI/save_map.png)


**The default save path is in the software running directory.**

### 4.2 Navigation

![Map Navigation](../../../resourse/20-myAgv2023/AGV_UI/navagation_en.png "Map Navigation")  

### Preconditions

#### 1、Copy and paste the saved map file into this path

 > /home/ubuntu/myagv_ros/src/myagv_navigation/map/

![File Manager](../../../resourse/20-myAgv2023/AGV_UI/file_2.png)

#### 2、modify the launch file

1. Click to open Visual Studio Code in the top left corner to open the code editor.  
![vscode Icon](../../../resourse/20-myAgv2023/AGV_UI/vscode_icon.png)


2. Open the navigation_active.launch file in /home/ubuntu/myagv_ros/src/myagv_navigation/launch/ path.  
![modify launchfile1](../../../resourse/20-myAgv2023/AGV_UI/modify_launch1.png)


3、Replace the myroom2.yaml in line 5 with our own map file name map.yaml.  
![modify launch file2](../../../resourse/20-myAgv2023/AGV_UI/modify_launch2.png)


4、Save the modified file and exit (VScode is more memory intensive when running, it is recommended to close VScode after modifying the code, otherwise the running carsystem will be very laggy, you can also use vim and other lightweight editors.)

**After following the above steps, click the corresponding button according to the desired navigation method.**  
**A Rviz simulation window will open. Note: It is best to place the initial position of the car at the starting position of the car when we build the map.**

### Adjust

If the car on the Rviz interface does not correspond to the actual car, click "2D Pose Estimate" on the top toolbar to adjust, so that the car on the Rviz interface and the realized car can correspond, and navigate after adjustment.

![Run launch File1](../../../resourse/20-myAgv2023/AGV_UI/run_launch1.jpg)  

1、Click on "2D Nav Goal" in the top toolbar.

![Run launch File3](../../../resourse/20-myAgv2023/AGV_UI/run_launch3.png)  

2、Click on the point we want to reach on the map, the carwill start towards the target point, and you can also see in the rviz a planned path of the carbetween the starting point and the target point, the carwill move along the route to the target point.

![Run launch File4](../../../resourse/20-myAgv2023/AGV_UI/run_launch4.jpg)  

**Limit:**

* You can only choose one of the two methods: navigation and 3D navigation. If you need to use another one, please close the current one.
* Mapping cannot be opened after the navigation is turned on. If you need to build a map, please close the navigation.

## 5、 LED light Control

![LED Light](../../../resourse/20-myAgv2023/AGV_UI/led_light_en.png "LED Light")

**Preconditions：** Close radar
Use the disc to select the light color, and drag the slider to change the brightness of the light color. The right side of the picture shows the corresponding HEX and RGB values.

## 6、 Testing FUnction

![Testing Function](../../../resourse/20-myAgv2023/AGV_UI/testing_en.png "Testing Function")
**Limit：During the test, the radar, basic control, and map navigation modules cannot be used.**

### 6.1 Motor

**Functions：** Check whether the motor can operate normally  
**Running：**  

* Select the 'Motor' from the drop-down box and click to start testing
* In this process, it is recommended to place myAgv on the ground for testing; during the process, it will go forward and backward for 4 seconds each, translate left and right for 4 seconds each, and rotate left and right for 8 seconds each.
* After all the above steps are executed, the detection is completed.

### 6.2 LED light

**Functions：** Check whether the Led light can operate normally  
**Running：**  

* Select the 'LED' from the drop-down box and click to start testing
* Switch the red, orange, yellow, green, blue, and purple colors in sequence. If the color switching can be observed normally, the LED light is used normally.
* The display time of each color is 1s. After all colors are displayed normally, the detection is completed.

### 6.3 3D Camera

**Functions：** Check whether the 3D camera can operate normally  
**Running：**  

* Select the '3D Camera' from the drop-down box and click to start testing
* A new window pops up to display the image captured by the camera; if the image can be displayed, the camera is operating normally.
* The screen is displayed for about 5 seconds, and then the window screen is automatically closed. Testing completed.


### 6.4 2D Camera

**Functions：** Check whether the 2D camera can operate normally  
**Running：**  

* Select the '2D Camera' from the drop-down box and click to start testing
* A new window pops up to display the image captured by the camera; if the image can be displayed, the camera is operating normally.
* The screen is displayed for about 5 seconds, and then the window screen is automatically closed. Testing completed.

### 6.5 Pump

**Functions：** Check whether the pump can operate normally  
**Running：**  

* Select the 'Pump' from the drop-down box and click to start testing
* The suction pump is turned on and turns off automatically after running for 4 seconds; at this time the detection is completed

### 6.6 Restore
![Restore Function](../../../resourse/20-myAgv2023/AGV_UI/restore_en.png "Restore FUnction")  
**Functions：**   Return the stalled motor to normal operation.
**Running：**  Clicked the button as the picture shows above.

* Select the 'Pump' from the drop-down box and click to start testing
* The suction pump is turned on and turns off automatically after running for 4 seconds; at this time the detection is completed

## 7. Log Area

![Log Area](../../../resourse/20-myAgv2023/AGV_UI/log_area_en.png "Log Area")

All the above operations will be displayed in the log area. Click the "Clear Button" on the right side of the icon to clear the current content.

## 8. Status Detection

![Status Detecting](../../../resourse/20-myAgv2023/AGV_UI/status_add_en.png "Status Information")

**1、 IP Address:** Show current IP address  
**2、 Battery Information:** Display the currently connected battery information  
- When connected, the green light and the corresponding power and voltage are displayed; when not connected, the display is gray and the value is 0.  

**3、 Motor Current:** Shows whether there is current flowing through and the electricity value  
- When the motor is in motion and there is current flowing through it, the motor will light up green and the page will display the current value; otherwise it will be gray.  

**4、 Radar Detection:** Shows whether radar is on  
- When the radar button is turned on, the green light turns on; when the radar button is turned off, the light turns off and turns gray.
