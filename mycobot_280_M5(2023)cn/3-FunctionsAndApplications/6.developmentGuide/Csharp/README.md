# **C#** 
**使用c#语言，您可以通过我们公司提供的c#动态库，进行自由开发(坐标控制、角度控制、io控制、夹爪控制等），控制我们公司已经研发出来的部分机器人。**<br>
支持的机械臂型号：**myCobot280、320和myPalletizer 260**。<br>

![pic](../../../resources/3-FunctionsAndApplications/6.developmentGuide/Csharp/Csharp.jpg)<br>

## C#是什么？

C#是微软公司发布的一种由C和C++衍生出来的面向对象的编程语言、运行于.NET Framework和.NET Core(完全开源，跨平台)之上的高级程序设计语言。<br>
C#与Java有着明显的不同，它借鉴了Delphi的一个特点，与COM（组件对象模型）是直接集成的，而且它是微软公司 .NET windows网络框架的主角。<br> 
C#使得C++程序员可以高效的开发程序，且因可调用由 C/C++ 编写的本机原生函数，而绝不损失C/C++原有的强大的功能。因为这种继承关系，C#与C/C++具有极大的相似性，熟悉类似语言的开发者可以很快的转向C#.<br>

**适用设备：**

- myCobot 280
  - myCobot 280 M5
  - myCobot 280 for Arduino <br>
  
- myCobot 320
  - myCobot 320 M5 <br>

**使用前提：**

- **M5** 系列版本， 底部 **M5Stack-basic** 烧录 **miniRobot**，选择 **Transponder** 功能，末端 **ATOM** 烧录最新版的 **atomMain** (出厂默认已烧录)

## 编程开发
## 部分集成开发环境（IDE)

**Visual Studio (Visual C#)**<br>
**MonoDevelop**<br>

## C#开发使用引导

您可以根据以下指引来使用 C#对我们的机械臂进行开发
1.[环境搭建](9.1-environment.md)

2.[编译运行](9.2-build.md)

3.[关节控制](9.3-angle.md)

4.[坐标控制](9.4-coord.md)

5.[IO控制](9.5-io.md)

6.[夹爪控制](9.6-gripper.md)

7.[api说明](9.7-API.md)

8.[使用案例](9.8-example.md)