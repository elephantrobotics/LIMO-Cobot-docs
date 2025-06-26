# 灵巧手

适配型号：myCobot 280、myPalletizer 260、mechArm 270

**产品图示**

![pi](../../resources\4-SupportAndService\Accessories\others/h1.jpg)


**规格说明：**

| 名称         | **mycobot灵巧手爪**                                          |
| ------------ | ------------------------------------------------------------ |
| 型号         | 灵巧手                                                       |
| 材料         | 3D打印                                                       |
| 尺寸         | 112×94×50mm                                                  |
| 颜色         | 白                                                           |
| 传动方式        | 齿轮＋连杆                                                |
| 夹持范围     | 20-45mm                                                      |
| 最大夹持力   | 100g                                                   |
| 固定方式     | 螺丝固定                                               |
| 使用环境要求 | 常温常压                                                     |
| 控制接口 | 串口控制                                                     |
| 适用设备     | ER myCobot 280 系列、 ER mechArm 270 系列、 ER myPalletizer 260 系列 |

**灵巧手：** 夹持物品时使用

**简介**

- 夹爪是一种可以实现类似人手功能的机器人部件。其结构较复杂、抓取物体牢固、不易掉落、易操作的优点。夹爪套件包括夹爪配件和乐高科技件，通过可编程系统控制机械臂的末端执行器，实现物件的抓取、多点定位等功能。

**工作原理**
- 由电机驱动，夹爪的指面作直线往复运动来实现张开或闭合动作的，电动夹爪的加减速可控，对工件的冲击可以减至最小，定位点位可控，夹持可控

**适用物体**

- 小方块

- 小球

- 长条物体

## 夹爪安装：
  将乐高连接件插入夹持器孔位中：
  ![](../../resources\4-SupportAndService\Accessories\others/h2.png)

  ![](../../resources\4-SupportAndService\Accessories\others/h3.jpg)

**电气连接**
  将安装好连接件的夹持器插入机械臂末端  
  ![](../../resources\4-SupportAndService\Accessories\others/h4.jpg)

## python编程控制

+ M5 版本

```python
 from pymycobot.mycobot280 import MyCobot280
 import time

 # 初始化一个MyCobot280对象
 mc = MyCobot280("COM3", 115200)

 mc.set_encoder(7,2048,40)#张开
 time.sleep(2)
 mc.set_encoder(7,2300,40)#握紧
 time.sleep(2)
 mc.set_encoder(7,2048,40)#握紧
```
+ Pi 版本
```python
     from pymycobot.mycobot280 import MyCobot280
     from pymycobot import PI_PORT, PI_BAUD  # 当使用树莓派版本的mycobot时可以引用这两个变量进行MyCobot初始化
     import time
        
     # 初始化一个MyCobot280对象
     mc = MyCobot280(PI_PORT, PI_BAUD)
     mc.set_encoder(7,2048,40)#张开
     time.sleep(2)
     mc.set_encoder(7,2300,40)#握紧
     time.sleep(2)
     mc.set_encoder(7,2048,40)#握紧
```