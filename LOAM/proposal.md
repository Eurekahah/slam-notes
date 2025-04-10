## LOAM 算法

paper: http://www.roboticsproceedings.org/rss10/p07.pdf

code: [HKUST-Aerial-Robotics/A-LOAM: Advanced implementation of LOAM (github.com)](https://github.com/HKUST-Aerial-Robotics/A-LOAM)

 [cgbcgb/A-LOAM-NOTED: Chinese annotated version of A-LOAM (github.com)](https://github.com/cgbcgb/A-LOAM-NOTED)

### 1. 概要

高频率低精度的里程计算法；一组是：低频率高精度的建图算法。最后将两个算法结合，进行实时建图。

### 2.里程计

由于机器人的运动，激光里程计直接获得的数据与实际数据点位置存在差异，因此需要进行修正。

#### 特征点提取

主要提取边缘点和平面点，

1. 计算曲率以设定的阈值区分，值大的为边缘点（如墙角），用于匹配线段。值小的的平面点（如地面），用于匹配平面块。
2. 为使得特征点均匀，将扫描scan分为若干区域，每个区域提取一定数量限制的点，并进行极大值抑制
3. 舍弃不可靠的平行点和遮挡点

#### 帧间匹配

- **运动估计**：
	将当前帧的边缘/平面点与上一帧对应特征匹配，最小化点到线（边缘）或点到面（平面）的距离，通过非线性优化求解位姿变换（旋转矩阵+平移向量）。

- **运动畸变校正**：
	激光雷达扫描时自身可能运动，导致点云畸变。LOAM根据估计的运动插值每个点的位置，消除畸变。

#### 建图与全局优化

- **地图融合**：
	将优化后的点云特征与全局地图匹配，进一步优化位姿，减少累积误差。
- **体素滤波**：
	对全局地图降采样，保持数据结构紧凑。

#### 优势与局限

- **优势**：
	- 实时性高，适合自动驾驶等场景。
	- 在结构化环境（如城市道路）中精度突出。
- **局限**：
	- 依赖环境特征，在空旷或动态场景中易失效。
	- 无闭环检测（后续改进算法如LeGO-LOAM加入此功能）。



~~~bash
docker run -it --gpus all --network host -e DISPLAY=host.docker.internal:0 -v F:/ros-slam/ws:/home/eureka/ws --name ros-melodic osrf/ros:melodic-desktop /bin/bash
~~~

