# Introduction to Motor PID

Modification of the PID parameters can be a trade-off between the control accuracy of the robotic arm and the stability of the movement, we provide two sets of PID parameters, which are suitable for occasions requiring high stability of the movement, and for occasions requiring high precision of the movement.

### Applies to PID parameters with smooth motion, where motion accuracy is affected by false positives:

    '''
    This document is applicable to the myCobot 280 series of robotic arms. 
    The function is to modify the joint motor configuration parameters 
    and verify the modification results.Please ensure that the robot 
    control port is not occupied when using it. If you encounter failure, 
    please run the file again.

    #Import dependent library files.
    import time
    from pymycobot import *

    #Define data address and data.

    #Define the serial port of the robotic arm，Please check your robot model and fill in the corresponding content.
    # _port = '/dev/ttyAMA0'
    _port = 'COM30'
    _baud = 115200

    #Instantiate a hardware serial port. 
    try:
        mc = MyCobot280(_port, _baud)
    except Exception as e:
        print(e)
        print("Error: The current serial port can not be used, please check whether the serial port serial number is correct, after confirming that there is no error, please re-run the program.")
        exit()


    #Loop modification and display modification results.
    #joint_id = 1 - 6.
    for i in range(1,6):
        mc.set_servo_data(i,23,0)
        time.sleep(1)
        print(mc.get_servo_data(i,23))
    input("The program ends, please press any key to exit.")
    exit()


### PID parameters suitable for high-precision scenarios will cause the arm to continuously adjust the steady state error:

    '''
    This document is applicable to the myCobot 280 series of robotic arms. 
    The function is to modify the joint motor configuration parameters 
    and verify the modification results.Please ensure that the robot 
    control port is not occupied when using it. If you encounter failure, 
    please run the file again.

    #Import dependent library files.
    import time
    from pymycobot import *

    #Define data address and data. 

    #Define the serial port of the robotic arm，Please check your robot model and fill in the corresponding content.
    # _port = '/dev/ttyAMA0'
    _port = 'COM30'
    _baud = 115200

    #Instantiate a hardware serial port. 
    try:
        mc = MyCobot280(_port, _baud)
    except Exception as e:
        print(e)
        print("Error: The current serial port is not available, please check whether the serial port serial number is correct or not, after confirming that there is no error, please re-run the program.")
        exit()


    #Loop modification and display modification results. 
    #joint_id = 1 - 6.
    for i in range(1,6):
        mc.set_servo_data(i,23,4)
        time.sleep(1)
        print(mc.get_servo_data(i,23))
    input("The program ends, please press any key to exit.")
    exit()


