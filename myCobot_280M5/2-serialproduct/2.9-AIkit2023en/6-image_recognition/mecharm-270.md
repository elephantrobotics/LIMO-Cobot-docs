
# Recognize image cards

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This case uses the eye-to-hand mode, uses the camera, loads the model data trained by Tensorflow through OpenCV, recognizes the image block and locates the position of the image block in the video. Through the relevant points, the space coordinate position of the block relative to the robot arm is calculated. Set up a set of related actions for the robot arm, and put the identified object into the bucket. In the following chapters, the code implementation process of the entire case will be introduced in detail.


### **1 Camera Adjustment**

 First, you need to use python to run OpenVideo.py under the aikit_V2 package. If the enabled camera is a computer camera, cap_num needs to be modified. For details, please refer to: **Precautions. Make sure that the camera completely covers the entire recognition area, and the recognition area is square** in the video, as shown in the figure below. If the recognition area does not meet the requirements in the video, the camera position needs to be adjusted.

**M5 version:**

* Open a command prompt terminal (shortcut Win+R, enter "cmd" to access the terminal). Switch to the directory path where "aikit_V2" is located, then enter the target folder.

```bash
cd Desktop/aikit_V2/AiKit_270M5/
```

* Enter the following command to open the camera for adjustment

```bash
python scripts/OpenVideo.py
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/color-1.png
width ="500"  align = "center">

**Raspberry Pi version:**

 * Open a console terminal (shortcut key Ctrl+Alt+T), enter the target folder

```bash
cd ~/aikit_V2/AiKit_270Pi/
```

* Enter the following command to open the camera for adjustment

```bash
python scripts/OpenVideo.py
```

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/color-1.png
width ="500"  align = "center">

### **2 Add new image**

**M5 version:**

* Open a command prompt terminal (shortcut Win+R, enter "cmd" to access the terminal). Switch to the directory path where "aikit_V2" is located, then enter the target folder.

```bash
cd Desktop/aikit_V2/AiKit_270M5/
```

* Enter the following command to start the process of adding images.

```bash
python scripts/add_img.py
```

**Raspberry Pi version:**

<video id="my-video" class="video-js" controls preload="auto" width="100%" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_270pi_add_img.mp4" type='video/mp4' >
</video>

 * Open a console terminal (shortcut key Ctrl+Alt+T), enter the target folder

```bash
cd ~/aikit_V2/AiKit_270Pi/
```

* Enter the following command to start the process of adding images.

```bash
python scripts/add_img.py
```

* Operate according to the prompts entered by the terminal, and capture the image in the second image box that pops up.

* After the image capture area is completed, press the Enter key, and according to the terminal prompt, enter a number (1~4) to save to the folder corresponding to the image, and press the Enter key to save it to the corresponding folder.

### **3 Case Reproduction**

**M5 version:**

* Open a command prompt terminal (shortcut Win+R, enter "cmd" to access the terminal). Switch to the directory path where "aikit_V2" is located, then enter the target folder.

```bash
cd Desktop/aikit_V2/AiKit_270M5/
```

- Then enter the following command to start the image recognition program.

```bash
python scripts/aikit_img.py
```

**Raspberry Pi version:**

<video id="my-video" class="video-js" controls preload="auto" width="100%" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_270pi_img.mp4" type='video/mp4' >
</video>

- Open a console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>), enter the following command to enter the target folder:

```bash
cd ~/aikit_V2/AiKit_270Pi
```

- Then enter the following command to start the image recognition program.

```bash
python scripts/aikit_img.py
```

- When the command terminal shows ok and the camera window can be opened normally, it means that the program runs successfully. At this time, the identifiable objects can be placed in the recognition area for recognition and capture.


**Precautions**

1. When the camera does not automatically frame the recognition area correctly, you need to close the program, adjust the position of the camera, and move the camera to the left or right.
2. If the command terminal does not display ok, and the picture cannot be recognized, you need to move the camera slightly backward or forward, and the program can run normally when the command terminal displays ok.
3. Since the recognition method has been changed, please make sure that there is a folder for storing pictures and pictures that need to be recognized under the code path. If not, you can use `python scripts/add_img.py` to add pictures.
4. OpenCV color recognition will be affected by the environment, and the recognition effect will be greatly reduced in a darker environment.
