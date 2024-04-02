# Hardware Structure

## **1 Robot Torso Construction**

### 1.1 Components of the Robot Joints

  ![Image of myArm's joint components](../../resourse/2-serialproduct/2.12-myArm/myarmmaxsize.png)

> Note: The 7th axis is an end rotation joint with no actual length; the diagram only indicates the lengths for joints 1-6. The joints are ordered from bottom to top as 1-7.

### 1.2 Working Space Range

- Operational Space
  
  The operational space of myArm is a spherical space with a radius of 310mm centered on Axis 2.

- Singular Position

  When all six joints are at 0°, the robotic arm is in a singular position.
  
  ![Image of singular position](../../resourse/2-serialproduct/2.12-myArm/matlab/奇异位置.png)

- Recommended Coordinate Motion Space

  It is recommended to control the coordinates in the following posture:
  
  ![Image of recommended posture](../../resourse/2-serialproduct/2.12-myArm/matlab/推荐姿态.png)

  The active space under this posture is as follows:

  ![Image of active space](../../resourse/2-serialproduct/2.12-myArm/matlab/活动空间.png)

  The cross-section of this active space is as follows:

  ![Image of recommended active space](../../resourse/2-serialproduct/2.12-myArm/matlab/推荐活动空间.png)

  The coordinate motion range in this posture can be approximately expressed as: \( 150^2 < x^2 + y^2 < 250^2 \)

### 1.3 Range of Joint Movement

- Joint Limitations

| Joint       | Range          |
| :----------:| :------------: |
| J1          | -160 ~ +160    |
| J2          | -80 ~ +80      |
| J3          | -165 ~ +165    |
| J4          | -100 ~ +80     |
| J5          | -165 ~ +165    |
| J6          | -110 ~ +110    |
| J7          | -165 ~ +165    |

## **2 Base and Tool Interface**

### 2.1 Base Fixation Interface

  ![Image of base size](../../resourse/2-serialproduct/2.12-myArm/myarmBaseSize.jpg)

> The base can be secured using various methods, currently offering LEGO connectors and screw locking options. It can be used with a G-type base or a large suction cup base.

### 2.2 Tool Extension Interface

  ![Image of tool size](../../resourse/2-serialproduct/2.12-myArm/ToolSize.jpg)

> The end can be secured using various methods, currently offering LEGO connectors and screw locking options. It can be used with myCobot series end accessories or user DIY accessories.

## 3 Precautions for Use

- Shell Material Environmental Requirements

| Working Environment | Conditions                                            |
| :------------------ | :---------------------------------------------------- |
| Temperature         | 0°C~45°C                                              |
| Relative Humidity   | 20%~70%                                               |
| Indoor/Outdoor      | Indoor                                                |
| Other Requirements  | - Avoid direct sunlight.<br />- Keep away from dust, fumes, salt, metal particles, etc.<br />- Keep away from flammable and corrosive liquids and gases.<br />- Do not come into contact with water.<br />- Do not transmit shocks and vibrations.<br />- Stay away from strong electromagnetic interference sources.|

---
