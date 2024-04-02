The screen that comes with myBuddy can display a variety of expressions through the python interface

Instructions：

1. Download and unzip [video file](https://github.com/elephantrobotics/pymycobot/blob/main/demo/mybuddy_demo/emoticon.zip) and [case code](https://github.com/elephantrobotics/pymycobot/blob/main/demo/mybuddy_demo/mybuddy_emoticon_demo.py) into the mybuddy system

2. Change the case file,Replace `/home/er/pymycobot/emo/face_video_3_2.mp4` with the decompressed video file path
    ```python
    from pymycobot import MyBuddyEmoticon
    import time

    # [video_path, Playback_duration(s)]
    video1 = ["/home/er/pymycobot/emo/face_video_3_2.mp4", 10]

    datas = [video1]

    me = MyBuddyEmoticon(datas)
    ...
    ```
3. Execute mybuddy_emoticon_demo.py


# API description：

## MyBuddyEmoticon(file_path: list = [], window_size: tuple = (), loop=False)
API for playing emoticons

* **Parameters**

    **file_path (list)**: `[[path, time]]`The absolute path of facial expression video and the length of time to play.Time in seconds.
    **window_size (tuple)**: `(Length, width) `Size of the playback window (default is full screen).
    **loop (bool)**: Loop playback or not (default False. only once by default).

### file_path()
Get Playfile List
* **Return**
  * video path list

### add_file_path(path_time)
Add Playback File
* **Parameters**
    **path_time(list)**: `[path, time]` The video address to be added and the running time

### del_file_path(index)
Delete the element with the specified subscript in the playlist list
* **Parameters**

    **index(int)**:: The subscript of the element in the playlist to be deleted

### pause()
Pause playback

### run()
Continue playing

### start()
start playing video

### join()
Wait for the thread playing the video to finish.