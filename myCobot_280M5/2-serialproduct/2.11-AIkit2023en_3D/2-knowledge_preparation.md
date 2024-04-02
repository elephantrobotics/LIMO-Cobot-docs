
## 1 OpenCV simple use

### 1.1 What is OpenCV

The full name of openCV is Open Source Computer Vision Library. It is an open source computer vision library of Intel (Intel), which consists of a series of C functions and C++ classes, and realizes many general algorithms in image processing and computer vision.

### 1.2 Installation and use of OpenCV

**Windows**

Open a console terminal (shortcut key Win+R, enter cmd, enter the terminal), enter the following command:

```bash
# The version numbers of the two need to be consistent, and version 4.6.0.66 is installed here
pip install opencv-python==4.6.0.66
pip install opencv-contrib-python==4.6.0.66
```

- Installation Verification

```bash
# You can also view other python libraries format: pip show library name
pip show opencv-python
pip show opencv-contrib-python
```

<img src =../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装3.png
width ="500"  align = "center">

<img src =../../resourse/13-AdvancedKit/AiKitV2.0/opencv安装4.png
width ="500"  align = "center">

**Linux**

Open a console terminal (shortcut key Ctrl+Alt+T), enter the command:

```bash
# The version numbers of the two need to be consistent, and version 4.6.0.66 is installed here
pip install opencv-python==4.6.0.66
pip install opencv-contrib-python==4.6.0.66
```

**simple use**

```bash
import cv2 
def openCamera():
    print('opencv version',cv2.__version__)
    print("Keyboard ESC to exit")

    cap = cv2.VideoCapture(0) # Linux
    # cap = cv2.VideoCapture(1) # Windows
    while cap.isOpened():
        sucess,frame = cap.read()
        if sucess:
            cv2.imshow("frame",frame)
            if cv2.waitKey(10)==27:
                break
    cap.release()
    cv2.destroyAllWindows()


if __name__=="__main__":
    openCamera()

```

## 2 Color recognition

### 2.1 Knowledge Supplement

Difference and Relationship between RGB and HSV Color Models:

- RGB
  - The RGB color model is an industry-standard color representation.
  - It creates various colors by changing the intensity of the red, green, and blue color channels and overlaying them.
  - Each of the red, green, and blue color channels has 256 levels of brightness.

- HSV
  - HSV stands for Hue, Saturation, and Value.
  - Hue represents the wavelength of light reflected or emitted by an object, often identified by color names such as red, orange, or green, measured in degrees from 0 to 360.
  - Saturation, also known as chroma, refers to the intensity or purity of a color, and its values range from 0% to 100%.
  - Value represents the brightness of the color, with values ranging from 0% to 100%.

- Differences and connections
  - In computer vision, the realization of scenes requires separation of color components and intensities, for example robustness to lighting changes or removal of shadows.
  - Unlike RGB, HSV separates luminance, or image intensity, from chrominance, or color information. Better feature extraction and lighting invariance or visualization.

### 2.2 Get BGR value

```bash
import cv2
# open camera
cap = cv2.VideoCapture(0)
ret,img = cap.read()
# Get the position information of the mouse click
def getposBgr(event, x, y, flags, param):
    if event == cv2.EVENT_LBUTTONDOWN:
        print("Bgr is", img[y, x])
cv2.imshow('image', img)
cv2.setMouseCallback("image", getposBgr)
cv2.waitKey(0)
```

RGB to HSV conversion：https://www.rapidtables.com/convert/color/rgb-to-hsv.html

### 2.3 Do color recognition

script file：color_detect.py

## 3 shape recognition

### 3.1 Do shape recognition

script file：shape_detect.py

## 4 YOLOV8 recognition

### 4.1 Perform yolov8 recognition

**Note:** The model is the best.pt model trained according to the official instructions. Users can train the data set by themselves and save the model as a .pt file for real-time recognition.

script file：yolov8_detect.py
