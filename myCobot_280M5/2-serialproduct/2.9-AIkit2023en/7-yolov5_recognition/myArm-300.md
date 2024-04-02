
# yolov5 image recognition

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This case uses the eye-to-hand mode, uses the camera to take pictures, loads the yolov5 model data through OpenCV, recognizes the image block and locates the position of the image block in the recognition area. Through the relevant points, the space coordinate position of the block relative to the robot arm is calculated. Set a set of related actions for the robot arm, and put the recognized object into the corresponding area.

### **1 Camera Adjustment**

 First, you need to use python to run OpenVideo.py under the aikit_V2 package. If the enabled camera is a computer camera, cap_num needs to be modified. For details, please refer to: **Precautions. Make sure that the camera completely covers the entire recognition area, and the recognition area is square** in the video, as shown in the figure below. If the recognition area does not meet the requirements in the video, the camera position needs to be adjusted.

**Raspberry Pi version:**

 * Open a console terminal (shortcut key Ctrl+Alt+T), enter the target folder

```bash
cd ~/aikit_V2/myArm-300PI/
```

* Enter the following command to open the camera for adjustment

```bash
python scripts/OpenVideo.py
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/color-1.png
width ="500"  align = "center">

### **2 Case Reproduction**

**Raspberry Pi version:**

<video id="my-video" class="video-js" controls preload="auto" width="100%" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/13-AdvancedKit/AiKitV2.0/myarm-yolov5.mp4" type='video/mp4' >
</video>

- Open a console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>), enter the following command to enter the target folder:

```bash
cd ~/aikit_V2/myArm_300PI
```

- Then enter the following command to start the yolov5 recognition program.

```bash
python scripts/yolov5_img.py
```

- When the camera window can be opened normally, it means that the program is running successfully. At this time, you can place the identifiable object in the recognition area, and take pictures and intercept according to the terminal prompts. When the command terminal shows ok, it means that yolov5 is recognizing and grasping, and the robot arm is completed. After a single capture, press the space bar for the next image recognition.


**Precautions**

1. If the command terminal does not display ok, and the picture cannot be recognized, you need to move the camera slightly backward or forward, and the program can run normally when the command terminal displays ok.

2. In order to better recognize the picture, you need to **reverse the object in the recognition area**.

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/yolov5图片1.png
width ="500"  align = "center">