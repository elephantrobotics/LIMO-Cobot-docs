# myCobot 摄像模组 v2.0

**适配型号**：myCobot 280、myPalletizer 260、mechArm 270

**产品图示**
![pi](../../resources\4-SupportAndService\Accessories\others/c1.jpg)

**规格说明：**

| 名称             | myCobot 摄像模组 v2.0                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------ |
| 型号             | myCobot_cameraHolder_J6                                                                    |
| 颜色             | 白色（默认）                                                                               |
| 材料             | ABS 注塑                                                                                   |
| 尺寸             | 83*64*16                                                                                   |
| USB 协议         | USB2.0 HS/FS                                                                               |
| 镜头焦距         | 标配 1.7mm                                                                                 |
| 视场角度         | 约 60°                                                                                     |
| 支持的系统       | Win7/8/10、Linux、MAC                                                                      |
| 支持的分辨率       | 2592x1944，2560x1440，2048x1536，1920x1080，1280x72，1024x768，800x600，640x480，640x360，352x288，320x240，176x144                                          |
| 使用寿命         | 两年                                                                                       |
| 固定方式         | 乐高连接件                                                                                 |
| 使用环境要求     | 常温常压                                                                                   |
| 适用设备 support | ER myCobot 280 系列 ，ER myPalletizer 260 系列， ER mechArm 270 系列， ER myBuddy 280 系列 |

**摄像头法兰 :** 机器视觉

**简介**

- USB 高清摄像头可搭配吸泵、自适应夹爪、人工智能套装等，eye in hand 实现精确定位与标定。

**安装使用**

- 检查配件包东西是否齐全：乐高连接件、带 usb 线的摄像头模组
  ![alt text](../../resources\4-SupportAndService\Accessories\others/c2.jpg)

- 摄像头安装：

  结构安装：

  将乐高连接件插入摄像模组预留的插孔中：
  ![](../../resources\4-SupportAndService\Accessories\others/c3.jpg)

  将插好连接件的摄像模组对准机械臂末端插孔插入：
  ![](../../resources\4-SupportAndService\Accessories\others/c4.jpg)

  电气连接：

  将 USB 线插入底座 USB 接口：
  ![](../../resources\4-SupportAndService\Accessories\others/c5.jpg)
  
## 编程开发：


 > 代码如下：

```python
python
import cv2
import numpy as np

cap = cv2.VideoCapture(0) # “0”，根据查询到的摄像设备号来定

while(True):
    ret, frame = cap.read()

    # gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    cv2.show('frame', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()

```

