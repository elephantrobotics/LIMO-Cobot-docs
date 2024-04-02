# IO control

IO is the input and output of data. There are multiple pins on the M5Stack-basic and Atom of our robot arm. The input and output modes can be set through the following function interface.
<img src =../../../resourse/17-myBuddy/Python/p7.png
width ="600"  align = "center">

# Atom IO

### set_pin_mode(id, pin_no, pin_mode)

Set the state mode of the specified pin in atom.

* **Parameters**

  * **id** – 1/2 (L/R)

  * **pin_no** (_int_) – pin number (1 - 5).

  * **pin_mode** (_int_) – 0 - input, 1 - output

### set_digital_output(id, pin_no, pin_signal)

Set atom IO output level

* **Parameters**

  * **id** – 1/2 (L/R)

  * **pin_no** (_int_) – 1 - 5

  * **pin_signal** (_int_) – 0 / 1

### get_digital_input(id, pin_no)

singal value

* **Parameters**

  * **id** – 1/2 (L/R)

  * **pin_no** (_int_) – 1 - 5

### set_pwm_output(id, channel, frequency, pin_val)

PWM control

* **Parameters**

  * **id** – 1/2 (L/R)

  * **channel** (_int_) – IO number (1 - 5).

  * **frequency** (_int_) – clock frequency (0/1: 0 - 1Mhz 1 - 10Mhz)

  * **pin_val** (_int_) – Duty cycle 0 ~ 100: 0 ~ 100%

# Raspberry Pi IO


> These interfaces are based on RPi.GPIO
### set_gpio_input(pin)

Set GPIO input value.

* **Parameters**

    **pin** – (int)pin number.

### set_gpio_mode(pin_no, mode)

Init GPIO module, and set BCM mode.

* **Parameters**

  * **pin_no** – (int)pin number.

  * **mode** – 0 - input 1 - output

### set_gpio_output(pin, v)

Set GPIO output value.

* **Parameters**

  * **pin** – (int)pin number.

  * **v** – (int) 0 / 1

### set_gpio_pwm(pin, baud, dc)

Set GPIO PWM value.

* **Parameters**

  * **pin** – (int)pin number.

  * **baud** – (int) 10 - 1000000

  * **dc** – (int) 0 - 100