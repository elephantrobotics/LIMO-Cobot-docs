# myCobot camera module v2.0

**Applicable models**: myCobot 280, myPalletizer 260, mechArm 270

**Product image**
![pi](../../resources\4-SupportAndService\Accessories\others/c1.jpg)

**Specifications:**

| Name | myCobot camera module v2.0 |
| ---------------- | ------------------------------------------------------------------------------------------ |
| Model | myCobot_cameraHolder_J6 |
| Color | White (default) |
| Material | ABS injection molding |
| Size | 83*64*16 |
| USB protocol | USB2.0 HS/FS |
| Lens focal length | Standard 1.7mm |
| Field of view | About 60° |
| Supported systems | Win7/8/10, Linux, MAC |
| Supported resolutions | 2592x1944, 2560x1440, 2048x1536, 1920x1080, 1280x72, 1024x768, 800x600, 640x480, 640x360, 352x288, 320x240, 176x144 |
| Service life | Two years |
| Fixing method | Lego connector |
| Environment requirements | Normal temperature and pressure |
| Applicable equipment support | ER myCobot 280 series, ER myPalletizer 260 series, ER mechArm 270 series, ER myBuddy 280 series |

**Camera flange:** Machine vision

**Introduction**

- USB high-definition camera can be used with suction pump, adaptive gripper, artificial intelligence kit, etc., to achieve precise positioning and calibration with eye in hand.

**Installation and Use**

- Check if the accessories package is complete: Lego connector, camera module with USB cable
![alt text](../../resources\4-SupportAndService\Accessories\others/c2.jpg)

- Camera installation:

Structural installation:

Insert the Lego connector into the reserved socket of the camera module:
![](../../resources\4-SupportAndService\Accessories\others/c3.jpg)

Align the camera module with the connector into the socket at the end of the robot arm:
![](../../resources\4-SupportAndService\Accessories\others/c4.jpg)

Electrical connection:

Insert the USB cable into the USB port of the base:
![](../../resources\4-SupportAndService\Accessories\others/c5.jpg)

## Programming development:

> The code is as follows:

```python
python
import cv2
import numpy as np

cap = cv2.VideoCapture(0) # "0", determined by the camera device number queried

while(True):
ret, frame = cap.read()

# gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

cv2.show('frame', frame)
if cv2.waitKey(1) & 0xFF == ord('q'):
break

cap.release()
cv2.destroyAllWindows()

```