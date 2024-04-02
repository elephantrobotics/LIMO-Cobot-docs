# Bluetooth control

> Note: The Bluetooth server will be automatically closed after the client connection ends, and it needs to be reopened when it is used again (it is best not to actively close the server, which may cause it to fail to open next time)
# start the server
1.Double click to open this software on the desktop

<img src =../../../resourse/17-myBuddy/Python/p1.jpg
width ="600"  align = "center">

2.Select Transponder, the port is /dev/ttyACM0, click Connect

<img src =../../../resourse/17-myBuddy/Python/p2.jpg
width ="600"  align = "center">

3.Select "Wlan Socket"

<img src =../../../resourse/17-myBuddy/Python/p5.jpg
width ="600"  align = "center">

4.Click "OPEN" to open the server

<img src =../../../resourse/17-myBuddy/Python/p6.jpg
width ="600"  align = "center">



If the server starts successfully, you can start using it

# Client

> Note: Please install **pybluez2** before using it, you can install it by command: pip install pybluez2==0.40

```python
from pymycobot import MyBuddyBlueTooth

mst = MyBuddyBlueTooth("00:00:00:00:00:00", 1)
mst.connect("/dev/ttyACM0", "115200")

print(mst.get_angles(1))
```