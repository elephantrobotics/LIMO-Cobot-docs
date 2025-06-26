# 柔性夹爪 - 张脚式

**适配型号**： myCobot 280、myPalletizer 260、mechArm 270、myBuddy 280

## **产品图示**

> ![alt text](../../resources\4-SupportAndService\Accessories\grip/Z1.jpg)
> ![alt text](../../resources\4-SupportAndService\Accessories\grip/Z2.jpg)

**规格说明：**

| 名称         | mycobot280 张角式夹爪                                                                      |
| ------------ | ------------------------------------------------------------------------------------------ |
| 型号 model   | myCobot 张角式夹爪                                                                         |
| 工艺         | 光敏树脂                                                                                   |
| 颜色         | 白色                                                                                       |
| 重复精度     | ±1mm                                                                                       |
| 使用寿命     | 一年                                                                                       |
| 驱动方式     | 电动 electric                                                                              |
| 固定方式     | 乐高连接件                                                                                 |
| 使用环境要求 | 常温常压                                                                                   |
| 控制接口     | 串口控制                                                                                   |
| 适用设备     | ER myCobot 280 系列 ，ER myPalletizer 260 系列， ER mechArm 270 系列 ，ER myBuddy 280 系列 |

**柔性夹爪:** 夹取物体使用

**简介**

- 传统工业吸盘需要吸取物料的平整表面，在越来越多的工况中，吸取表面容易损伤面板或元器件，柔触夹爪捏边抓取，轻松无痕无损搬运面板，确保产品表面无瑕疵，提升良品率。
- 柔触夹爪的模块化设计，自重轻，可以按照面板尺寸自由排列组合。
- 传统气缸的夹持力普遍较大，且力度难以控制，夹持面板的边缘容易夹伤夹翘，柔性夹爪的单指夹持力精准可控，不会夹伤脆弱工件。

**工作原理**

- 柔性夹爪是研究人员模仿海星腕足的形态，研发出的一种创新型仿生柔性夹具。软爪的“手指”是由高分子硅胶柔性材料制作而成，通过充气实现弯曲形变，能够像海星一样，自适应地包覆住目标物体，可完成对异形、易损物品的柔性、无损抓取 。

**适用物体**

- 合理大小内的任意形状物体

**安装使用**

- 检查配件包东西是否齐全：乐高连接件、带连接线的夹爪、连接线延长线
>   ![](../../resources\4-SupportAndService\Accessories\grip/Z3.jpg)

- 夹爪安装：

  结构安装：将乐高连接件插入夹爪预留的插孔中，根据需要可以选择两个不同方向进行安装：
 >  ![](../../resources\4-SupportAndService\Accessories\grip/Z4.jpg)

  将插好连接件的夹爪对准机械臂末端插孔插入：

 >  ![](../../resources\4-SupportAndService\Accessories\grip/Z5.jpg)

- 电气连接：

  将延长线与夹爪连接：
> ![](../../resources\4-SupportAndService\Accessories\grip/Z6.jpg)
 插入机械臂控制接口：

> ![](../../resources\4-SupportAndService\Accessories\grip/Z7.png)  


> ![](../../resources\4-SupportAndService\Accessories\grip/Z8.jpg)  
<br>

## 编程开发

- M5 版本：

```python
from pymycobot import MyCobot280
import time

# 初始化一个MyCobot280对象
mc = MyCobot280("COM3", 115200)

# 以下三种方式均可控制夹爪打开-关闭-打开
# 方式一：
mc.set_gripper_state(0, 80)
time.sleep(3)
mc.set_gripper_state(1, 80)
time.sleep(3)
mc.set_gripper_state(0, 80)
time.sleep(3)

# 方式二：
# mc.set_gripper_value(100, 80)
# time.sleep(3)
# mc.set_gripper_value(0, 80)
# time.sleep(3)
# mc.set_gripper_value(100, 80)
# time.sleep(3)

# 方式三：
# mc.set_encoder(7, 2048, 20)
# time.sleep(3)
# mc.set_encoder(7, 1500, 20)
# time.sleep(3)
# mc.set_encoder(7, 2048, 20)
# time.sleep(3)
```

- Pi 版本：

```python
from pymycobot import MyCobot280
from pymycobot import PI_PORT, PI_BAUD  # 当使用树莓派版本的mycobot时，可以引用这两个变量进行MyCobot初始化
import time

# 初始化一个MyCobot280对象
mc = MyCobot280(PI_PORT, PI_BAUD)

# 以下三种方式均可控制夹爪打开-关闭-打开
# 方式一：
mc.set_gripper_state(0, 80)
time.sleep(3)
mc.set_gripper_state(1, 80)
time.sleep(3)
mc.set_gripper_state(0, 80)
time.sleep(3)

# 方式二：
# mc.set_gripper_value(100, 80)
# time.sleep(3)
# mc.set_gripper_value(0, 80)
# time.sleep(3)
# mc.set_gripper_value(100, 80)
# time.sleep(3)

# 方式三：
# mc.set_encoder(7, 2048, 20)
# time.sleep(3)
# mc.set_encoder(7, 1500, 20)
# time.sleep(3)
# mc.set_encoder(7, 2048, 20)
# time.sleep(3)
```

保存文件并关闭，返回命令行终端，输入：

```bash
python grip.py
```

> 可以看到夹爪打开-关闭-打开
