## 夹爪控制

使用Python控制夹爪之前，需要先在机械臂上安装连接好夹爪。不同夹爪适配不同的机械臂（具体适配信息请参考**产品配件**。

> **注意：**
>
> MyCobot 280自适应夹爪将夹爪插在Atom上面的引脚上，具体看下图：
>
> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\Jaw/夹爪1.jpg" style="zoom: 67%;" />
>


### 夹爪控制

**`is_gripper_moving( )`**

- **功能：** 判断夹爪是否正在运行
- **返回值：**
  - `0 ` ：表示机械臂的夹爪没有运行
  - `1` ：表示机械臂的夹爪正在运行
  - `-1`：表示出错

**`set_gripper_value(value, speed, gripper_type=None)`**

- **功能：** 让夹爪以指定的速度转动到指定的位置
- **参数说明：**
  - `value`：表示夹爪所要到达的位置，取值范围 0~100
  - `speed`：表示以多少的速度转动，取值范围 0~100
  - `gripper_type`：夹爪类型，默认是自适应夹爪
    - `1`: 自适应夹爪
    - `3`: 平行夹爪
    - `4`: 柔性夹爪
- **返回值：** 1

**`get_gripper_value(gripper_type=None)`**

- **功能：** 获取夹爪的当前位置数据信息
- **参数说明：**
  - `gripper_type`：夹爪类型，默认是自适应夹爪
    - `1`: 自适应夹爪
    - `3`: 平行夹爪
    - `4`: 柔性夹爪
- **返回值：** 夹爪的数据信息

**`set_gripper_state(flag, speed， _type=None)`**

- **功能：** 让夹爪以指定的速度进入到指定的状态
- **参数说明：**
  - `flag`：1 表示夹爪合拢状态，0 表示夹爪打开状态。
  - `speed`：表示以多快的速度达到指定的状态，取值范围 0~100
  - `_type`: 夹爪类型，默认是自适应夹爪
    - `1`: 自适应夹爪
    - `2`: 五指灵巧手
    - `3`: 平行夹爪
    - `4`: 柔性夹爪
- **返回值：** 1

**`set_HTS_gripper_torque(torque)`**

- **功能：** 设置自适应夹爪力矩
- **参数说明：**
  - `torque`：150 ~ 900
- **返回值：** 0 - 设置失败；1 - 设置成功

**`get_HTS_gripper_torque()`**

- **功能：** 获取自适应夹爪力矩
- **返回值：** 150 ~ 900

**`get_gripper_protect_current()`**

- **功能：** 获取夹爪保护电流
- **返回值：** 1 ~ 500

**`init_gripper()`**

- **功能：** 初始化夹爪
- **返回值：** 0 - 初始化失败；1 -初始化成功

**`set_gripper_protect_current(current)`**

- **功能：** 设置夹爪保护电流
- **参数说明：**
  - `current`：1 ~ 500
- **返回值：** 0 - 初始化失败；1 -初始化成功

### 案例

```python
from pymycobot.mycobot280 import MyCobot280
import time
#输入以上代码导入工程所需要的包

def gripper_test(mc):
    print("Start check IO part of api\n")
    # 检测夹爪是否正在移动
    flag = mc.is_gripper_moving()
    print("Is gripper moving: {}".format(flag))
    time.sleep(1)

    # Set the current position to (2048).
    # Use it when you are sure you need it.
    # Gripper has been initialized for a long time. Generally, there
    # is no need to change the method.
    # mc.set_gripper_ini()
    # 设置关节点1，让其转动到2048这个位置，速度20
    mc.set_encoder(1, 2048, 20)
    time.sleep(2)
    # 设置六个关节位，让机械臂以20的速度转动到该位置
    mc.set_encoders([1024, 1024, 1024, 1024, 1024, 1024], 20)
    time.sleep(3)
 

    # 以70的速度让夹爪到达100状态
    mc.set_gripper_value(100, 70)
    time.sleep(3)
    # 以70的速度让夹爪到达0状态
    mc.set_gripper_value(0, 70)
    time.sleep(3)

    # 设置夹爪的状态，让其以70的速度快速打开爪子
    mc.set_gripper_state(0, 70)
    time.sleep(3)
    # 设置夹爪的状态，让其以70的速度快速收拢爪子
    mc.set_gripper_state(1, 70)
    time.sleep(3)

    # 获取夹爪的值
    print("")
    print(mc.get_gripper_value())


if __name__ == "__main__":
    # MyCobot 类初始化需要两个参数：
    #   第一个是串口字符串， 如：
    #       linux： "/dev/ttyUSB0"
    #       windows: "COM3"
    #   第二个是波特率：
    #       M5版本为： 115200
    #
    #   Example:
    #       mycobot-M5:
    #           linux:
    #              mc = MyCobot("/dev/ttyUSB0", 115200)
    #           windows:
    #              mc = MyCobot("COM3", 115200)

    # 初始化一个MyCobot280对象
    # 下面为M5版本创建对象代码
    mc = MyCobot280('COM3', 115200)
    # 让其移动到零位
    mc.set_encoders([2048, 2048, 2048, 2048, 2048, 2048], 20)
    time.sleep(3)
    gripper_test(mc)
```
