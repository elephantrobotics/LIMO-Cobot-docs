# 环境搭建

pymycobot 是一个和 myCobot 进行串口通讯的 Python 包，支持 Python2、Python3.5 及之后版本。

在使用 pymycobot控制机械臂之前需要搭建Python环境，下面就对Python的下载安装做出详细说明。



## Python下载和安装

**适用设备：**

* myCobot 280：
  * **myCobot 280 M5**
  * myCobot 280 PI
  * myCobot 280 Jetson Nano
  * myCobot 280 for Arduino 

目前，Python有两个版本，一个是`2.x`版，一个是`3.x`版，这两个版本是不兼容的。由于`3.x`版越来越普及，我们的教程将以最新的`3.10.7`版本为例进行说明。



### 安装Python

> **注意：**安装之前，请先确认您的电脑是64位还是32位。右键点击`我的电脑`，选择`属性`。如下图显示是64位的操作系统，所以选择64位的Python安装包。
>
> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/电脑位数1.jpg" style="zoom: 67%;" />
>
> <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/电脑位数2.jpg" style="zoom: 67%;" />



* **Python官方下载地址： https://www.python.org/downloads/**

* **点击`Downloads`选项，开始下载Python，点击`Add Python 3.10 to PATH`,点击`Install Now`，开始安装Python**

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pythondownload1.jpg" style="zoom: 33%;" />

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pythondownload2.jpg" style="zoom: 50%;" />

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pythondownload3.jpg" style="zoom: 50%;" />



* **出现“Setup was successful”提示，说明安装完成**

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pythondownload4.jpg" style="zoom: 50%;" />



### 运行Python
安装成功后，打开命令提示符窗口（Win+R，输入cmd回车），敲入`python`后，会出现两种情况。

**情况一：**

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/运行python1.jpg" style="zoom: 50%;" />

出现图片中的提示表示Python安装成功。

出现提示符`>>>` 就表示我们已经在Python交互式环境中了，可以输入任何Python代码，回车后会立刻得到执行结果。

**情况二：** 

假如输入错误（比如输入pythonn），则会出现错误提示：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/运行python2.jpg" style="zoom: 50%;" />

>  **注意：**出现错误的信息一般都是没有配置环境变量导致的，可以参考**下文 配置环境变量**修改环境变量。



### 配置环境变量
由于Windows会根据一个Path的环境变量设定的路径去查找python.exe，如果没找到，就会报错。因此，如果安装时漏掉了勾选`Add Python 3.10 to PATH`，则需要手动把python.exe所在的路径添加到Path中，或者重新安装一遍Python，记得勾选上`Add Python 3.10 to PATH`选项即可。

以下是手动添加python.exe所在的路径步骤。

* 右键我的电脑–>选择属性–>选择高级系统设置–>选择右下角的环境变量：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/环境变量.jpg" style="zoom: 50%;" />



* 环境变量主要有包括用户变量和系统变量，需要设置的环境变量就在这两个变量中。如下图所示：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/添加path.jpg" style="zoom: 50%;" />



* 用户变量是将自己的下载的程序可以在cmd命令中使用。把程序的绝对路径写到用户变量中即可使用，如下图所示：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/绝对路径.jpg" style="zoom: 50%;" />



<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/添加path.jpg" style="zoom: 50%;" />



* 以上步骤完成后，打开命令提示符窗口（Win+R，再输入cmd，回车），敲入Python，出现下图中的提示表示成功：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/路径添加成功.jpg" style="zoom: 50%;" />



## PyCharm安装和使用

PyCharm是一款功能强大的Python编辑器，具有跨平台性。首先介绍PyCharm在Windows系统中的安装步骤。

**下载地址：** **https://www.jetbrains.com/pycharm/download/#section=windows**

### 下载安装

* 进入该网站后，我们会看到如下界面：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm界面.jpg" style="zoom: 40%;" />

根据界面介绍下载文件，Professional表示专业版，Community是社区版，推荐安装社区版，因为是免费使用的。

* 下载好之后开始安装，点击`Next`：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm下载1.jpg" style="zoom: 50%;" />

* 按照个人喜好选择相应选项，然后点击`Next`：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm下载2.jpg" style="zoom: 50%;" />

* 出现下图界面继续点击`Next`：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm下载3.jpg" style="zoom: 50%;" />

* 点击`Finish`结束安装：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm下载4.jpg" style="zoom: 50%;" />



### 创建项目

PyCharm安装完成之后进入该软件，创建第一个程序。

* 单击桌面上的PyCharm图标，进入到PyCharm中，如下图所示，点击`New Project`：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/创建新项目1.jpg" style="zoom: 33%;" />

* 点击之后找到`Interpreter`，开始对解释器进行设置，点击`Add Interpreter`：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/解释器1.jpg" style="zoom: 50%;" />

* 点击`New`，找到python.exe存储位置，勾选`Inherit global site-package`选项：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/解释器2.jpg" style="zoom: 33%;" />

* 设置`Location`。Location是存储PyCharm项目的地方，可根据需要自行选择。

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/location1.jpg" style="zoom: 33%;" />

* 新建PyCharm文件。右击箭头指向的文档图标，点击`New`，点击`Python File`，新建成功。

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharmfile1.jpg" style="zoom: 33%;" />



* 命名Python File：

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharmfile2.jpg" style="zoom: 67%;" />



* 文件创建成功后便进入如下的界面，便可以编写自己的程序了

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pycharm界面展示.jpg" style="zoom: 33%;" />



### 使用之前

* 固件烧录。固件是指设备内部保存的设备“驱动程序”。操作系统只有通过固件才能按照标准的设备驱动实现特定机器的运行动作。不同版本的机械臂需要烧录不同的固件（可以参考 [**MyStudio**](../../5.BasicFunction/5.2-Softwarelnstructions/README.md)章节）。
  * **M5版本**底部的Basic需要烧录minirobot。烧录完成后选择**Transponder**功能（该功能用于接收转发底部Basic发送的指令，从而执行目标动作），点击`Press A`，出现**Atom：OK**提示信息即为成功。此外，M5版本末端 Atom 烧录最新版的 atomMain，出厂默认已烧录，无需自行烧录。
* pymycobot安装。打开一个控制台终端(快捷键Win+R,输入cmd进入终端)，输入以下命令：

```python
pip install pymycobot --upgrade --user
```

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pymycobot安装.jpg" style="zoom: 67%;" />

出现了以下字样则证明pymycobot包安装成功

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pymycobot安装完成.png" style="zoom: 67%;" />

* 源码安装。打开一个控制台终端(快捷键Win+R,输入cmd进入终端)，输入以下命令即可安装：

```python
git clone https://github.com/elephantrobotics/pymycobot.git <your-path>   
#其中<your-path>填写你的安装地址，不填默认在当前路径
								
cd <your-path>/pymycobot	
#进入到下载包的pymycobot文件夹

#根据你的python版本运行下面其一命令	
# Install
 python2 setup.py install	
# or
 python3 setup.py install
```



## Python简单使用

上述准备工作完成之后，开始通过Python代码实现对机械臂的操控。这里以MyCobot 280 M5版本为例进行演示。

首先，打开您安装好的PyCharm，新建一个Python文件，输入以下代码，导入我们的库：

```python
from pymycobot import MyCobot280
```

**注意：**

1. 如果输入`from pymycobot.mycobot280 import MyCobot280`，字体下方没有出现红色波浪线证明已经安装成功可以使用了，如果出现红色波浪线可以参考[**如何安装API库** ](https://www.cnblogs.com/xiaoguan-bky/p/11184740.html)，[**如何调用API库**](https://jingyan.baidu.com/article/25648fc1e86917d191fd009d.html)。

2. 如果不想通过上述命令安装API库，可以通过以下github下载项目到本地。 

   首先，进入项目地址：**https://github.com/elephantrobotics/pymycobot** 。然后点击网页右边Code按钮，再点击Download ZIP下载到本地，将压缩包pymycobot文件项目中的 pymycobot文件夹放入你python依赖库目录中，就可以直接导入使用。

   <img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/pymycobotgithub.jpg" style="zoom: 33%;" />



### 简单演示

在PyCharm中新建一个 Python 文件，输入以下代码可执行 LED 闪烁（myCobot 280-M5可参考以下代码）。

> **注意：** 各款设备的对应的波特率不尽相同，使用时请查阅资料了解其波特率，串口编号可通过 [计算器设备管理器](https://docs.elephantrobotics.com/docs/gitbook/4-BasicApplication/4.1-myStudio/4.1.1-myStudio_download_driverinstalled.html#4113-%E5%A6%82%E4%BD%95%E5%8C%BA%E5%88%86cp210x%E5%92%8Ccp34x%E8%8A%AF%E7%89%87) 或串口助手进行查看。

以下是myCobot相应的代码。

* **myCobot**

```python
from pymycobot.mycobot280 import MyCobot280
import time
#以上需写在代码开头，意为导入项目包

# MyCobot280 类初始化需要两个参数：串口和波特率
#   第一个是串口字符串， 如：
#       linux： "/dev/ttyUSB0"
#       windows: "COM3"
#   第二个是波特率：
#       M5版本为： 115200
#   以下为如:
#       mycobot-M5:
#           linux:
#              mc = MyCobot280("/dev/ttyUSB0", 115200)
#           windows:
#              mc = MyCobot280("COM3", 115200)

# 初始化一个MyCobot280对象
# 下面为 windows版本创建对象代码
mc = MyCobot280("COM3", 115200)

i = 7
#循环7次
while i > 0:							
    mc.set_color(0,0,255) #蓝灯亮
    time.sleep(2)	#等2秒				
    mc.set_color(255,0,0) #红灯亮
    time.sleep(2)	#等2秒
    mc.set_color(0,255,0) #绿灯亮
    time.sleep(2)	#等2秒
    i -= 1
```

如果在执行代码时出现以下报错，请仔细查阅程序中的串口号是否正确。查询自己电脑的串口号并在程序中修改为您所查询到的串口号即可解决此报错问题。若程序正常运行，但机械臂无任何反应，请检测波特率是否填写正确。

<img src="../../../resources\3-FunctionsAndApplications\6.developmentGuide\python\build/串口报错.png" style="zoom: 60%;" />
