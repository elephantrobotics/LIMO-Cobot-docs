# TCP/IP

TCP/IP传输协议，即传输控制/网络协议，也叫作网络通讯协议。它是在网络的使用中的最基本的通信协议，对互联网中各部分进行通信的标准和方法进行了规定。用户可以通过机械臂的IP地址连接机械臂，达到无需连接USB端口也可以远程操作机械臂的效果。

## myCobot

**在使用机械臂之前请确保Basic固件与Atom固件已经烧录（烧录详情请参考：5.2软件使用说明章节）**

### 连接步骤

#### 创建一个默认网络

myCobot 280 m5 机械臂使用TCP/IP时，会用默认密码“mycobot123”去连接“MyCobotWiFi2.4G”的一个网络。

此时我们可以用手机创建一个热点，把热点网络名称改为“MyCobotWiFi2.4G”，密码设置为“mycobot123”，开启热点后，机械臂使用TCP/IP功能，就会自动连上手机热点。后续只要在同一局域网内，设备之间就可以进行网络通信。

同理路由器也是这样设置，把路由器的网络名称和密码设置好，机械臂开启TCP/IP功能，就会连上路由器。

需要注意的一点，myCobot 280 m5 机械臂，仅支持2.4 GHz的网络频带。支持不了5 GHz的网络频带，下面以手机热点为例。

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/热点设置2.jpg" style="zoom: 25%;" />

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/热点设置1.jpg" style="zoom: 25%;" />

#### TCP/IP功能开启

如图所示，机械臂通过按键点击Transponder->WLAN Server，连接成功的话会显示IP和端口号。如果连接失败，请检测网络名称和密码有没有设置正确。

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP//Transponder.jpg)

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/WLAN Server1.jpg" style="zoom: 25%;" />

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP//wificonnecting.jpg" style="zoom: 25%;" />

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/移动链接.jpg" style="zoom: 25%;" />

#### 连接其他网络

如果需要连接其他网络，可以通过下载我司提供的[myBlockly软件](https://www.elephantrobotics.com/download/)去连接其他网络。

**注意**：280 m5断电无法保存已连接WIFI账号和密码，280 m5断电重启后还是会去连接默认WIFI账号“MyCobotWiFi2.4G”和密码“mycobot123”，连接其他网络需要再次设置WIFI账号和密码。

**Step 1:** 将PC和myCobot 280 m5进行连接

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/OtherNetworks.png)

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/OtherNetworks2.png)

**Step 2:** 打开myBlockly，设置280 m5要连接的WIFI账号和密码，然后点击运行。

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/OtherNetworks3.png)

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/OtherNetworks4.png)

**Step 3:** 操作步骤如下：Transponder -> WLAN Server，此时机械臂就会去连接“agilex-desktop”的网络。

![](../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/Transponder.jpg)

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/WLAN Server1.jpg" style="zoom: 25%;" />

### 2 案例

在手机热点下，机械臂成功启动TCP/IP功能后，机械臂会显示出IP和端口。需要记住该IP和端口。

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\TCPorIP/移动链接.jpg" style="zoom: 25%;" />

PC电脑，连上跟机械臂同一个手机热点，调用python的驱动库，就可以通过机械臂的IP地址连接机械臂，达到无需连接USB端口也可以远程操作机械臂的效果。

```python
from pymycobot import MyCobot280Socket
# 默认使用9000端口
#其中"172.20.10.14"为机械臂IP，请自行输入你的机械臂IP
mc = MyCobot280Socket("172.20.10.14",9000)  

#连接正常就可以对机械臂进行控制操作
mc.send_angles([0,0,0,0,0,0],20)
res = mc.get_angles()
print(res)

...
```

