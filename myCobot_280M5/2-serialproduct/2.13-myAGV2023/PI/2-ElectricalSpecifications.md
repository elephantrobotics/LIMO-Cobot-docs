# Electrical Interface of myAGV 2023

## 1 Surface electrical interface

### 1.1 Surface electrical interface introduction

* The surface interface is shown in Figure 1:

  <img src="../../../resourse/20-myAgv2023/PI/dianqi_1.png" style="zoom:100%;" /> 

  Figure 1 Surface electrical interface
  - ① Power switch button
  - ② Power supply interface of robot arm
  - ③ IO interface group 
  - ④ USB2.0 interface
  - ⑤ HDMI interface
  - ⑥ The network interface
  - ⑦ Power charging interface

### 1.2 Surface electrical interface description

> **Notice:** Functional interface group is Dupont interface of 2.54mm, and 2.54mm Dupont wire can be used externally.

* A. Power switch button: Press down to turn on myAGV.

* B. Power supply interface of robot arm: banana plug female, model XT30UPB-F, to supply power to my series robot arm (12V 5A).

* C. IO interface group：The IO interface group is Dupont interface of 2.54mm, and 2.54mm Dupont wire can be used externally.The IO interface definition is shown in Table 1:

<center>Table 1</center>

| Label | Signal | Type | Function | Notes |
| :---: | :----: | :--: | :------: | :----: |
| 3.3 | 3.3V | P | DC 3.3V |  |
| 17 | GPIO17 | I/O | GPIO17 |  |
| 27 | GPIO27 | I/O | GPIO27 |  |
| 22 | GPIO22 | I/O | GPIO22 |  |
| 10 | GPIO10 | I/O | GPIO10 |  |
| 9 | GPIO9 | I/O | GPIO9 |  |
| 11 | GPIO11 | I/O | GPIO11 |  |
| G | GND  | p | GND |  |
| 18 | GPIO18 | I/O | GPIO18 |  |
| 23 | GPIO23 | I/O | GPIO23 |  |
| 24 | GPIO24 | I/O | GPIO24 |  |
| 25 | GPIO25 | I/O | GPIO25 |  |
| 08 | GPIO8 | I/O | GPIO8 |  |
| 07 | GPIO7 | I/O | GPIO7 |  |

> **Notice:** 
> 1. I: As input only
> 
> 2. I/O: This function signal includes input and output combination.
> 
> 3. When the single tube corner is set as the output terminal, it will output 3.3V voltage.
> 
> 4. The source current of a single tube angle decreases with the increase of the number of pins, from about 40mA to 29mA.
> 
> 5. If a certain GPIO is set to the output mode and outputs a high level signal, the circuit connected to the LED is shown in Figure 2 , and the LED will light up.
> 
> <img src="../../../resourse/20-myAgv2023/PI/IO.png" style="zoom:100%;" />
>
>Figure 2 IO interface usage mode
> 
> 6. In the case of using other functions, the IO function is unavailable, and the other function table of the function interface is shown in Figure 3 .
> 
> <img src="../../../resourse/20-myAgv2023/PI/IO_other.png" style="zoom:100%;" />
> 
> Figure 3 Other functions of the IO interface

* D. USB2.0 interface：Serial port with the standard of main line for 2.0 interface. The USB port is used to copy program files and connect peripherals such as mouse and keyboard.

  <img src="../../../resourse/20-myAgv2023/PI/USB.png" style="zoom:100%;" /> 

  Figure 4 USB 2.0 interface

* E. HDMI interface: The HDMI D-type port connects with the monitor. 

  <img src="../../../resourse/20-myAgv2023/PI/HDMI.png" style="zoom:100%;" /> 

  Figure 5 HDMI interface

* F. The network interface: Ports for network data connection. Ethernet interfaces can be used for communication between a PC and a robot system or for Ethernet communication with other devices.

  <img src="../../../resourse/20-myAgv2023/PI/Ethernet.png" style="zoom:100%;" />

  Figure 6 The network interface

* G. Power charging interface: Use DC 2.5*5.5 power port; The myAGV can be charged using the factory-supplied 12.6V2A DC power adapter.

## 2 Magazine electrical interface

### 2.1 Introduction to the electrical interface of the magazine

* The electrical interface of the magazine is shown in Figure 7:

  ![图片](../../../resourse/20-myAgv2023/PI/pump.png)

  Figure 7 Magazine electrical interface
  - ① Standby battery port
  - ② Suction pump interface

### 2.2 Magazine electrical interface description

* A. Standby battery port: Connects the standby battery.

* B. Suction pump interface: connect suction pump, control suction pump work.