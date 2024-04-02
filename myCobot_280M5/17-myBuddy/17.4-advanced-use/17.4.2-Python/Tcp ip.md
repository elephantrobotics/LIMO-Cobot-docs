> Note: This function must be used under the same network

# start the server
1.Double click to open this software on the desktop

<img src =../../../resourse/17-myBuddy/Python/p1.jpg
width ="600"  align = "center">

2.Select Transponder, the port is /dev/ttyACM0, click Connect

<img src =../../../resourse/17-myBuddy/Python/p2.jpg
width ="600"  align = "center">

3.Select "Wlan Socket"

<img src =../../../resourse/17-myBuddy/Python/p3.jpg
width ="600"  align = "center">

4.Click "OPEN" to open the server

<img src =../../../resourse/17-myBuddy/Python/p4.jpg
width ="600"  align = "center">

# Client connection

```python
from pymycobot import MyBuddySocket

mst = MyBuddySocket("192.168.0.1", 9000)
mst.connect("/dev/ttyACM0", "115200")

print(mst.get_angles(1))
```