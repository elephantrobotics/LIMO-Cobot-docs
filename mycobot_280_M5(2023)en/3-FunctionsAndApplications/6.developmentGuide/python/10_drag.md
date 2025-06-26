# Drag teaching

Trajectory recording (including adaptive grippers) and playback can be realized.

> Python version drag teaching only supports Pi and Jetson Nano versions in 280, 270, and 320 models.

## Usage:

- 1. Download [drag teaching Python code file](https://github.com/elephantrobotics/pymycobot/blob/main/demo/drag_trial_teaching.py)
- 2. Copy the downloaded file to the robot system.
- 3. Open the terminal and run the file:
```bash
python drag_trial_teaching.py
```


After the file is run:
- 3.1 Select the robot port
- 3.2 Enter the baud rate, the default is 1000000
  
| Machine model | Serial port number | Baud rate |
|:---------:| :--------:|:--------:|
|270 PI| /dev/ttyAMA0|1000000|
|280 PI| /dev/ttyAMA0|1000000|
|320 PI| /dev/ttyAMA0|115200|
|280 Jetson Nano| /dev/ttyTHS1|1000000|
- 3.3 Select whether to debug or not. Debugging is not enabled by default.
- 3.4 Finally, enter the function selection list. Function selection is achieved through keyboard keys:
- `q`: Exit
- `r`: Start recording
- `c`: Stop recording
- `p`: Play once
- `P`: Loop playback / Stop playback
- `s`: Save the recording information of this time. The recording information will be saved to the record.txt file in the same directory as `drag_trial_teaching.py`
- `l`: Load the information in the record.txt file in the same directory as `drag_trial_teaching.py`
- `f`: Relax all joints of the robot arm