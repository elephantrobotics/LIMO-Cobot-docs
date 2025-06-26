## MoveIt2

### MoveIt2 简介

MoveIt2 是ROS2中的一个集成开发平台，由多种用于操纵机械臂的功能包组成，包括：运动规划、操作、控制、逆运动学、3D感知和碰撞检测等。

### 核心功能

1. **运动规划（Motion Planning）**  
   MoveIt 2 提供基于 OMPL（Open Motion Planning Library）和其他第三方库的运动规划能力，支持多种规划算法和约束。

2. **逆向运动学（Inverse Kinematics, IK）**  
   MoveIt 2 使用插件机制支持不同的 IK 解算器，能够快速计算机械臂的目标位姿。

3. **碰撞检测与避免（Collision Detection & Avoidance）**  
   MoveIt 2 内置强大的碰撞检测功能，确保机器人在规划和执行运动时不会与周围环境发生碰撞。

4. **动态场景感知（Dynamic Scene Awareness）**  
   MoveIt 2 支持动态更新环境模型，可以实时感知障碍物的变化。

5. **控制与执行（Control & Execution）**  
   MoveIt 2 提供运动控制接口，与机器人硬件紧密集成，确保规划路径可以准确执行。

6. **可视化工具（Visualization Tools）**  
   与 RViz 2 集成，支持直观的交互和调试功能，可以实时显示运动规划和执行过程。

### MoveIt 2 的优势

- **基于 ROS 2 的实时性支持**  
  ROS 2 的 DDS 通信架构赋能 MoveIt 2，在实时性和可靠性上有显著提升。

- **模块化设计**  
  MoveIt 2 采用模块化架构，支持用户根据需要加载或替换模块，提供极大的灵活性。

- **跨平台支持**  
  MoveIt 2 支持在多种操作系统（如 Ubuntu、Windows）和硬件平台上运行。

- **活跃的社区支持**  
  MoveIt 2 拥有一个全球化的开发者社区，持续提供更新、功能扩展和技术支持。

### 配置

1. URDF - 通用机器人描述格式。

2. SRDF - 包括机器人的关节组、虚拟关节和被动关节、机器人姿势、自碰撞，通常由用户使用 MoveIt2 设置助手创建。

3. MoveIt2 配置 - 包括关节限制、运动学、运动规划、感知和其他信息。这些组件的配置文件由MoveIt2设置助手自动生成 ([MoveIt2配置助手](https://moveit.picknik.ai/main/doc/examples/setup_assistant/setup_assistant_tutorial.html))，并存储在机器人的相应MoveIt2配置包的配置目录中。

## 如何使用MoveIt2

>>**注意：** 为了更好的运动规划效果，机械臂末端Atom固件版本为6.5，python驱动库pymycobot版本为3.5.3

`mycobot_ros2` 现已集成了 MoveIt2 部分。

打开命令行运行：
  
```bash
ros2 lanuch mycobot_280_moveit2 demo.launch.py
```

运行效果如下：  

<img src =../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/moveit2/moveit2_rviz2.png
width ="500"  align = "center">

如果需要让真实的机械臂同步执行计划，需要再打开一个命令行，运行：
  
```bash
ros2 run mycobot_280_moveit2_control sync_plan
```

案例演示：

<video id="my-video" class="video-js" controls preload="auto" width="100%"
poster="" data-setup='{"aspectRatio":"16:9"}'>
  <source src="../../../../../resources/3-FunctionsAndApplications/6.developmentGuide/ROS/ROS2/moveit2/280_ROS2_Moveit2_Case_Demo.mp4" type='video/mp4' >
</video>
