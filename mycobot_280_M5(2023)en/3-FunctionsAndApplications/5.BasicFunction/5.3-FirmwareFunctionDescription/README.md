# Factory firmware introduction

Only introduce the myCobot series, myPalletizer series and mechArm series, which are divided into two categories: microcontrollers and microprocessors.

- Microcontroller devices:
- myCobot 280 M5
- myCobot 320 M5
- myPalletizer 260 M5
- mechArm 27 M5
- Microprocessor devices
- myCobot 280 Pi
- myCobot 320 Pi
- mechArm 270 Pi

The difference between microprocessors and microcontrollers is mainly concentrated in three aspects: hardware structure, application field and instruction set characteristics:

- Hardware structure. The microprocessor is a single-chip CPU, while the microcontroller integrates the CPU and other circuits in an integrated circuit chip to form a complete microcomputer system. In addition to the CPU, the microcontroller also includes RAM, ROM, a serial interface, a parallel interface, a timer and an interrupt scheduling circuit.

- Application field. Microprocessors are usually used as CPUs in microcomputer systems. They are designed for such applications, which is also the advantage of microprocessors. However, microcontrollers are usually used in control-oriented applications, and the system design pursues miniaturization and minimizes the number of components. Microcontrollers are suitable for those occasions where input/output devices are controlled with very few components, while microprocessors are suitable for information processing in computer systems.

- Instruction set characteristics. Due to different applications, the instruction sets of microcontrollers and microprocessors are also different. The instruction set of microprocessors enhances processing capabilities, giving them powerful addressing modes and instructions suitable for operating large-scale data. Microprocessor instructions can operate on nibbles, bytes, words, and even double words. By using address pointers and address offsets, microprocessors provide addressing modes that can access large amounts of data. The self-increment and self-decrement modes make it very easy to access data in units of bytes, words, or double words.

## 1. Factory firmware for microcontrollers: miniRoboFlow
miniRoboFlow has four main functions:
- [Drag teaching](5.3.1-moving/5.3.1.1-micro_controller.md) (Maincontrol)
- Robot drag teaching, the operator can directly drag the robot joints to move to the ideal posture, and save the action in the machine through button operation. Collaborative robots are the earliest systems with this function. This teaching method can avoid the various shortcomings of traditional teaching and is a technology with great application prospects in robots.
- [Calibration](5.3.2-calibration/5.3.2.1-micro_controller.md) (Calliberation)
- Calibrating the robot arm is the prerequisite for precise control of the robot arm. Setting the joint zero position and initializing the motor potential value are the basis for subsequent advanced development.
- [Computer control](5.3.3-transponder/5.3.3.1-micro_controller.md)（Transponder)
- The timeliness of communication is very important for microcontroller robot arms. For microcontroller robot arms, we usually send control instructions to the M5Stack-basic at the bottom. Through communication forwarding, the end effector will parse the instructions and then execute the target action. At present, the communication methods of myCobot 280 are: serial communication, Bluetooth communication, and WIFI communication.
- [Connection detection](5.3.4-connection/5.3.4.1-micro_controller.md)（Information)
- Connection detection is a detection function for the connection status of the motor and Atom in the robot arm. This function is convenient for customers to troubleshoot equipment failures. In the connection detection, the device connection status of the robot arm is seen, including the connection of the servo and the communication status of the Atom. The current firmware version of the device will be displayed on the M5Stack-basic in the microcontroller device.