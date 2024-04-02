
# Identify AR code

This case uses the eye-to-hand mode, uses the camera, combines **Python+OpenCV**, performs attitude estimation through the ArUco marker in OpenCV, and frames the AR code that meets the situation, and calculates it through the relevant points The spatial coordinate position of the AR code relative to the robotic arm. Set a set of related actions for the robotic arm, and place them in different areas according to the recognized AR code.


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

### **2 Case Reproduction**

**Prerequisites**

**Flip the QR code board to the back and place it, or take two cards to cover the two QR codes on the board to prevent misidentification when starting the AR code program.**

<img src =../../../resourse/13-AdvancedKit/AiKitV2.0/260aruco-1.png
width ="500"  align = "center">

**M5 version:**

* Open a command prompt terminal (shortcut Win+R, enter "cmd" to access the terminal). Switch to the directory path where "aikit_V2" is located, then enter the target folder.

```bash
cd Desktop/aikit_V2/AiKit_270M5/
```

- Then enter the following command to start the AR code recognition program.

```bash
python scripts/aikit_encode.py
```

**Raspberry Pi version：**

<video id="my-video" class="video-js" controls preload="auto" width="100%" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../resourse/13-AdvancedKit/AiKitV2.0/aikit_270pi_encode.mp4" type='video/mp4' >
</video>

- Open a console terminal (shortcut key <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>), enter the following command to enter the target folder:

```bash
cd ~/aikit_V2/AiKit_270Pi
```

- Then enter the following command to start the AR code recognition program.

```bash
python scripts/aikit_encode.py
```

- When the command terminal shows `ok` and the camera window can be opened normally, it means that the program runs successfully. At this time, the identifiable objects can be placed in the recognition area for recognition and capture.

**Precautions**

1. When the camera does not automatically frame the recognition area correctly, you need to close the program, adjust the position of the camera, and move the camera to the left or right.
2. If the command terminal does not show ok, and the color cannot be recognized, you need to move the camera slightly backward or forward, and the program can run normally when the command terminal shows ok.
3. OpenCV color recognition will be affected by the environment, and the recognition effect will be greatly reduced in a darker environment.
