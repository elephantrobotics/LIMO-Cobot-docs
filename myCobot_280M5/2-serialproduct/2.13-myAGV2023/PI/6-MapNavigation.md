# myAGV 2023-Map Navigation

Previously, we have created a spatial map and obtained two map files: "map.pgm" and "map.yaml" located in the "~/myagv_ros/src/myagv_navigation/map" directory.

![地图保存终端2](../../../resourse/20-myAgv2023/PI/map_saver_2.png)

Now let's take a look at how to use the created map for navigation of the robot.

## 1. Modify Launch Files

1. Open and edit the "navigation_active.launch" file located in the "~/myagv_ros/src/myagv_navigation/launch/" directory.

```bash
cd ~/myagv_ros/src/myagv_navigation/launch
sudo gedit navigation_active.launch
```

![导航编辑文件](../../../resourse/20-myAgv2023/PI/navigation_edit_1.jpg)

2. Find the parameter "map_file" and replace "map.yaml" in "default="$(find myagv_navigation)/map/map.yaml" with the desired map parameter file. If you don't make any changes, it will default to loading the "map.yaml" file.

![导航编辑文件_2](../../../resourse/20-myAgv2023/PI/navigation_edit_1.png)

3. Save the modified file and exit.

## 2. Run the Launch File

1. After powering on the robot, open a terminal console (shortcut: <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the following command in the command line:

```bash
cd myagv_ros
roslaunch myagv_odometry myagv_active.launch 
```

2. Then, open another terminal console (shortcut: <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>) and enter the following command:

```bash
cd myagv_ros
roslaunch myagv_navigation navigation_active.launch
```

![导航终端显示](../../../resourse/20-myAgv2023/PI/navigation_terminal.png)

3. You will see that an Rviz simulation window has been opened.

**Note: It's best to place the robot's initial position at the starting position where we created the map. If you need to modify the starting position, please follow the steps below.**

Click on the "2D Pose Estimate" in the top toolbar to adjust the position so that the car in the Rviz interface matches the physical car. The terminal will then return the coordinates and heading angle of the car relative to the map.

![导航修改起始点](../../../resourse/20-myAgv2023/PI/navigation_modify_startpoint.png)

Open and edit the "navigation_active.launch" file located in "~/myagv_ros/src/myagv_navigation/launch/". Find the "amcl" node, and replace "initial_pose_x", "initial_pose_y", and "initial_pose_a" with the coordinates and heading angle returned by the terminal in that order. After launching "navigation_active.launch" again, the robot's starting position will be updated.

![导航修改起始点_2](../../../resourse/20-myAgv2023/PI/navigation_modify_startpoint_1.png)

4. Explanation of the Navigation Control Panel in the Bottom Left Corner

① Maximum Number of Target Points: You can set the maximum number of target points. The number of set target points cannot exceed this parameter (but can be fewer).

② Loop: If checked, after navigating to the last target point, the robot will navigate back to the first target point. For example: 1 -> 2 -> 3 -> 1 -> 2 -> 3 -> ... This option must be checked before starting navigation.

③ Task Target Point List: x/y/yaw, the pose (xy coordinates and yaw) of the given target points on the map.

- After setting the maximum number of target points and saving, this list will generate the corresponding number of entries.
- When providing a target point, the coordinates and orientation will be read here.

④ Start Navigation: Begin the task.

⑤ Cancel: Cancel the current target point navigation task, and the robot will stop moving. Clicking "Start Navigation" again will resume from the next target point.

Example: 1 -> 2 -> 3. If you click "Cancel" during the 1 -> 2 process, the robot will stop. Clicking "Start Navigation" again will make the robot go from the current position to 3.

⑥ Reset: Clears all current target points.

![导航运行图](../../../resourse/20-myAgv2023/PI/navigation.png)

5. Set the number of target points for the task, and click to confirm and save. Then, click on "2D Nav Goal" on the toolbar to define the target point on the map. (Each time you set a point, start by clicking "2D Nav Goal"). The target points differentiate orientation, with the arrowhead representing the vehicle's heading direction. Click "Start Navigation" to begin the navigation. In Rviz, you will see a planned path from the starting point to the target point, and the vehicle will move along this route to reach the destination.![导航运行图_2](../../../resourse/20-myAgv2023/PI/navigation_2.png)