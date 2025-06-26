# 出厂固件介绍

myCobot系列、myPalletizer系列以及mechArm系列的机械臂分为微控制器和微处理器两类。

- 微控制类设备：
  - **myCobot 280 M5**
  - myCobot 320 M5
  - myPalletizer 260 M5
  - mechArm 27 M5

## 微控制类设备出厂固件：miniRoboFlow
miniRoboFlow主要有四种功能：
- [拖动示教](./5.3.1-moving/5.3.1.1-micro_controller.md)（Maincontrol）
  - 机器人拖动示教，操作员可以直接拖着机器人各关节，运动到理想的姿态，通过按钮操作将动作保存在机器中。协作机器人是较早具有该功能的系统。这种示教方式可以避免传统示教的各种缺点，是机器人中一项很有应用前景的技术。
- [校准](./5.3.2-calibration/5.3.2.1-micro_controller.md)（Calliberation)
  - 校准机械臂是对机械臂精准控制的前提，设置关节零位，初始化电机的电位值是后续进行进阶开发的基础。
- [电脑控制](./5.3.3-transponder/5.3.3.1-micro_controller.md)（Transponder)
  - 通讯的时效性对于微控制器机械臂至关重要，对于微控制器机械臂来说，我们通常对底部的M5Stack-basic发送控制指令，通过通讯转发，末端执行器将对指令进行解析，继而执行目标动作。目前 myCobot 280的通讯方式有：串口通讯、蓝牙通讯、WIFI通讯。
- [连接检测](./5.3.4-connection/5.3.4.1-micro_controller.md)（Information)
  - 连接检测是一项用机械臂中电机以及Atom连接状态的检测功能。这项功能便于客户排除设备故障。  连接检测中看到机械臂的设备连接状态，包括舵机的连接以及Atom 的通讯状态。微控制器类设备中M5Stack-basic上会显示设备的当前固件版本。
