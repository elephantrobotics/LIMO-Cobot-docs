# 电机PID介绍

修改PID参数可以权衡机械臂控制精度与运动稳定性，我们提供了两套PID参数，分别适用于对运动稳定性要求高的场合，以及对运动精度要求高的场合

### 适用于运动流畅的PID参数，运动精度会受虚位影响：

    '''
    This document is applicable to the myCobot 280 series of robotic arms. 
    The function is to modify the joint motor configuration parameters 
    and verify the modification results.Please ensure that the robot 
    control port is not occupied when using it. If you encounter failure, 
    please run the file again.

    本文件适用于myCobot 280系列机械臂, 功能为修改关节电机配置参数补偿关节虚位,
    使用时请保证未占用机器人控制端口,如遇到失败请重新运行文件.
    '''

    #Import dependent library files. 导入相关库文件。
    import time
    from pymycobot import *

    #Define data address and data. 定于数据地址及内容。

    #Define the serial port of the robotic arm，Please check your robot model and fill in the corresponding content.
    #定义机器人串口配置数据，请检查你的机器人型号，并根据具体型号填写。
    # _port = '/dev/ttyAMA0'
    _port = 'COM30'
    _baud = 115200

    #Instantiate a hardware serial port. 实例化硬件串口。
    try:
        mc = MyCobot280(_port, _baud)
    except Exception as e:
        print(e)
        print("错误：当前串口无法使用，请检查串口序号是否正确，确认无误后请重新运行程序。")
        exit()


    #Loop modification and display modification results. 循环修改关节电机配置参数并校验是否修改成功。
    #joint_id = 1 - 6.
    for i in range(1,6):
        mc.set_servo_data(i,23,0)
        time.sleep(1)
        print(mc.get_servo_data(i,23))
    input("The program ends, please press any key to exit. 程序结束，请按任意键退出。")
    exit()


### 适用于高精度场景的PID参数,会令机械臂持续调节稳态误差：

    '''
    This document is applicable to the myCobot 280 series of robotic arms. 
    The function is to modify the joint motor configuration parameters 
    and verify the modification results.Please ensure that the robot 
    control port is not occupied when using it. If you encounter failure, 
    please run the file again.

    本文件适用于myCobot 280系列机械臂, 功能为修改关节电机配置参数补偿关节虚位,
    使用时请保证未占用机器人控制端口,如遇到失败请重新运行文件.
    '''

    #Import dependent library files. 导入相关库文件。
    import time
    from pymycobot import *

    #Define data address and data. 定于数据地址及内容。

    #Define the serial port of the robotic arm，Please check your robot model and fill in the corresponding content.
    #定义机器人串口配置数据，请检查你的机器人型号，并根据具体型号填写。
    # _port = '/dev/ttyAMA0'
    _port = 'COM30'
    _baud = 115200

    #Instantiate a hardware serial port. 实例化硬件串口。
    try:
        mc = MyCobot280(_port, _baud)
    except Exception as e:
        print(e)
        print("错误：当前串口无法使用，请检查串口序号是否正确，确认无误后请重新运行程序。")
        exit()


    #Loop modification and display modification results. 循环修改关节电机配置参数并校验是否修改成功。
    #joint_id = 1 - 6.
    for i in range(1,6):
        mc.set_servo_data(i,23,4)
        time.sleep(1)
        print(mc.get_servo_data(i,23))
    input("The program ends, please press any key to exit. 程序结束，请按任意键退出。")
    exit()


