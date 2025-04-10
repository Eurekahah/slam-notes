# 目标识别

2D-3D

1. 3D-BoundingBox + YOLO

3D

1. PointRCNN
2. PointPillars
3. Complex-YOLO
4. SECOND

要求：大致查看每种方案，至少实现其中一种方案的演示demo，目前不要求可以与ROS集成

# 仿真搭建

1. 构建可用地图城市道路环境，要求：可用的.world文件
2. 使用turtlebot输出雷达数据到ros系统，要求：使用命令`rostopic list`可查看到
3. 车辆可以操纵移动，目前可以尽停留在直线移动，未来将开发人工手动移动或者自动寻路

# 多车协作

1. 搭建基本的通信框架，实现两台机器在lego-loam上的同时建图（可查阅网络可能有现成的co版）

   