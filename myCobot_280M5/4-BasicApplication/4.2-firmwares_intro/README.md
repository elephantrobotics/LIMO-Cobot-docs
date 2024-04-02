# Factory firmware introduction

We divide the devices into two categories: **micro-controller** and **micro-CPU.** (Only introduce myCobot series, myPalletizer series, mechArm series products)

-   **Micro-controller devices**
  - **myCobot 280-M5**
  - **myCobot 320-M5**
  - **myPalletizer 260- M5**
  - **mechArm 270-M5**
  
-   **Micro-CPU devices**
  - **myCobot 280-Pi**
  - **myCobot 320-Pi**
  - **mechArm 270-Pi**

The difference between the micro-CPU and the micro-controller mainly focuses on three aspects: hardware structure, application fields and instruction set characteristics:

-   Hardware structure. The micro-CPU is a single-chip CPU, while the micro-controller integrates a CPU and other circuits in an  integrated circuit chip to form a complete microcomputer system. Beside the CPU, the micro-controller includes a RAM, ROM, serial    interface, parallel interface, timer, and interrupt scheduling circuit.

-   Application fields. The micro-CPU is usually used as a CPU in a microcomputer system, and they are designed for such application.This is just the advantage of the micro-CPU. However, the micro-controller is usually used in control-oriented applications, where system design seeks miniaturize and minimizes the number of components. The micro-controller is suitable for those applications  in which control of input/output devices is implemented with very few components, while the micro-CPU is suitable for information  processing in a computer system.

-   Instruction set characteristics. Due to different applications, the instruction set of the micro-controller is also different from the one of the micro-CPU. The instruction set of the micro-CPU enhances the processing function, making it have a powerful addressing mode and the instructions suitable for manipulating large amounts of  data. The instructions of the micro-CPU allow operation of nibbles,  bytes, words, and even double words. By using address pointers and offsets, the micro-CPU provides an addressing mode that allows access of large amounts of data. The auto-increment and auto-decrement modes make it easy to access data in the units of bytes, words, or double words.

Here you can gradually familiarize yourself with the robot arm through simple routines.

## 1 Factory firmware for micro-controller devices - miniRoboFlow

**miniRoboFlow** has four main functions: 
- [**Maincontrol**](https://docs.elephantrobotics.com/docs/myarm-pi-300-en/4-BasicApplication/4.2-firmwares_intro/4.2.1-moving/)
  - Robot drag teaching: The operator can drag robot joints directly to make them do ideal postures, and then save the actions in the robot through **button operation**. The cobot is a system that has this function earlier. This kind of teaching avoids various disadvantages of
  traditional teaching, so it is a prospective technology for robot applications. 
- [**Calibration**](https://docs.elephantrobotics.com/docs/myarm-pi-300-en/4-BasicApplication/4.2-firmwares_intro/4.2.2-calibration/)
  - Calibrating the robot arm is the precondition for precise control of the robot arm, and setting joint zero and initializing the potential of the motor are basic jobs for subsequent advanced development. 
- [**Transponder**](https://docs.elephantrobotics.com/docs/myarm-pi-300-en/4-BasicApplication/4.2-firmwares_intro/4.2.3-transponder/)
  - Communication timeliness is vital to the micro-controller robot arm.For such arm, we often send control instructions to **M5Stack-basic** at the bottom. Through communication forwarding, the end effector analyzes the instructions and then implements target actions. At present, **myCobot280** has three methods of communication: **serial port, Bluetooth, and WIFI**. 
- [**Information**](https://docs.elephantrobotics.com/docs/myarm-pi-300-en/4-BasicApplication/4.2-firmwares_intro/4.2.4-connection/)
  - Link test is a detection function that uses the motor in the robot arm and the connection state of **Atom**. The function allows the user to remove equipment faults easily. During the link test, the connection state of the equipment for the robot arm, including the **connection of the servo** and the **communication state of Atom** can be seen. In
  micro-controller devices, the versions of their current firmwares are shown on M5Stack-basic.

## 2 Factory firmware for micro-CPU devices- python demo

At present, the python demos that have been opened to micro-CPU devices are:
- [**drag\_trial\_teaching**](https://github.com/elephantrobotics/pymycobot/blob/main/demo/drag_trial_teaching.py)
  - [drag teaching](4.2.1-moving/4.2.1.2-micro_CPU.md)The operator can drag robot joints directly to make them do ideal postures, and then save the actions in the robot through **button operation**. The  cobot is a system that has this function earlier. This kind of teaching avoids various disadvantages of traditional teaching, so it is a prospective technology for robot applications. 
- [**rasp\_mycobot\_test\_gui**](https://github.com/elephantrobotics/pymycobot/blob/main/tests/rasp_mycobot_test_gui.py)
  - This python demo is a test tool for micro-CPU devices, including functions **robot arm** **calibration** and **connection detection**.
  - [**Robot arm calibration**](4.2.2-calibration/4.2.2.2-micro_CPU.md) Calibrating the robot arm is the precondition for precise control of the robot arm, and setting joint zero and initializing the potential of the motor are basic jobs for subsequent advanced development. 
  - [**Connection detection**](4.2.4-connection/4.2.4.2-micro_CPU.md) Link test is a detection function that uses the motor in the robot arm and the connection state of **Atom**. The function allows the user to remove equipment faults easily. During the link test, the connection state of the equipment for the robot arm, including the **connection of the servo** and the **communication state of Atom** can be seen. In micro-controller devices, the versions of their current firmwares are shown on M5Stack-basic.

