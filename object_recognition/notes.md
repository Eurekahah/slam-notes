# 目标识别

OpenPCDet：一个开源的目标识别框架，集合了众多目标识别算法，包括PointPillars，PointRCNN，并且有相应的预训练模型，在此基础上将其与ROS进行结合。

官方项目地址：https://github.com/open-mmlab/OpenPCDet，这是OpenMMLab做的，只训练模型可以只安装这个

ROS结合版本：https://github.com/Kin-Zhang/OpenPCDet_ros，这个就是给上面那个加了一个ROS的架子。

安装以上两个内容可以参考https://www.cnblogs.com/kin-zhang/p/17002980.html

数据集：KITTI：https://www.cvlibs.net/datasets/kitti/raw_data.php

> 使用KITTI数据集是raw模式，转换为bag数据播放需要使用官方提供的kitti2bag模块，使用pip install kitti2bag即可，参考https://blog.csdn.net/m0_45388819/article/details/108582312

以及我自行使用gazebo录制的数据

安装好后需要进行模型的训练。这是你俩要做的，我给你们提供数据集。

## 实验

模型：pv_rcnn_8369.pth 评分阈值：0.7

<img src="./assets/image-20250422202534371.png" alt="image-20250422202534371" style="zoom: 30%;" /><img src="./assets/image-20250422202759560.png" alt="image-20250422202759560" style="zoom:30%;" />

