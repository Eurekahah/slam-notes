所需要的库
Eigen (linear algebra library, tested on 3.2.9 & 3.3.4; elevation_mapping failed on 3.3.9)


[Cython](https://github.com/cython/cython) (C extensions for Python)
pip install cython


git clone https://github.com/borglab/gtsam.git -b 4.0.0-alpha2 && cd gtsam \
      && mkdir build && cd build && cmake .. && make install \


wget -O kindr.tar.gz https://github.com/ANYbotics/kindr/archive/refs/tags/1.2.0.tar.gz \
    && tar -xvzf kindr.tar.gz && cd kindr-1.2.0 && mkdir build && cd build \
    && cmake .. && make install -j8 


wget -O fftw.tar.gz http://fftw.org/fftw-3.3.10.tar.gz && tar -xvzf fftw.tar.gz \
    && cd fftw-3.3.10 && mkdir build && cd build && cmake .. \
    && make install -j8 


wget -O ceres.tar.gz https://github.com/ceres-solver/ceres-solver/archive/refs/tags/1.14.0.tar.gz && tar -xvzf ceres.tar.gz \
    && cd ceres-solver-1.14.0 && mkdir build && cd build && cmake .. \
    && make install -j8 
sudo apt install ros-$ROS_DISTRO-grid-map*
sudo apt install ros-$ROS_DISTRO-octomap*




git clone --recursive https://github.com/MaverickPeter/MR_SLAM.git
构建
cd Mapping && catkin_make -DBUILD_PYTHON_BINDINGS=ON
cd Localization && catkin_make




//增加回环检测
cd LoopDetection && catkin_make -DBUILD_PYTHON_BINDINGS=ON
cd fast_gicp python3 setup.py install --user
缺什么包pip3 安装即可 或者用conda也类似

//使用（ring ring++ disco）依赖cuda
安装cuda:11.1.1
pip3 config set global.index-url http://pypi.douban.com/simple
pip3 config set install.trusted-host pypi.douban.com

pip3 install torch==1.10.1+cu111 torchvision==0.11.2+cu111 torchaudio==0.10.1 -f https://download.pytorch.org/whl/cu111/torch_stable.html
pip3 install scipy open3d scikit-image alpha-transform

cd generate_bev_cython_binary && python3 setup.py install --user 或者加sudo
cd torch-radon && python3 setup.py install --user
 cd generate_bev_pointfeat_cython && python3 setup.py install --user 或者加sudo
cd LoopDetection/src/disco_ros/tools/multi-layer-polar-gpu/cython && python3 setup.py install --user 或者加sudo
//运行回环检测
rosrun disco_ros main.py（我目前报错 原因未知）

cd src/RING_ros
python main_SC.py

cd src/RING_ros
python main_RING.py

python main_RINGplusplus.py







rostopic pub /map_saving std_msgs/Bool "data: true" -1

存储地图



rosbag play loop-2.bag /livox/imu:=/robot_1/imu /livox/lidar:=/robot_1/pointcloud --clock --pause 
rosbag play loop-3.bag /livox/imu:=/robot_2/imu /livox/lidar:=/robot_2/pointcloud --clock --pause
rosbag play loop-4.bag /livox/imu:=/robot_3/imu /livox/lidar:=/robot_3/pointcloud --clock --pause
播放自制数据集



rosbag play robot_1.bag /livox/imu:=/robot_1/imu /livox/lidar:=/robot_1/pointcloud --clock --pause 
rosbag play robot_2.bag /livox/imu:=/robot_2/imu /livox/lidar:=/robot_2/pointcloud --clock --pause

rosbag play robot_3.bag /livox/imu:=/robot_2/imu /livox/lidar:=/robot_2/pointcloud --clock --pause



source devel/setup.bash 

roslaunch fast_lio robot_1.launch 

roslaunch fast_lio robot_2.launch 

roslaunch fast_lio robot_3.launch 



roslaunch global_manager global_manager.launch 



source ~/pyvenv/mr_slam_venv/bin/activate

python src/RING_ros/main_SC.py 



cd /media/eureka/Solid\ Disk/datasets/bags/





## 实验结果

### 1

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：ScanContext icp threshold=0.13

前端：fastlio2

![image-20250428201618180](./assets/image-20250428201618180.png)

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：RING++ icp threshold=0.15

前端：fastlio2

![image-20250428195856294](./assets/image-20250428195856294.png)

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：RING icp threshold=0.13

前端：fastlio2

![image-20250428200737306](./assets/image-20250428200737306.png)



## 2

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：ScanContext icp threshold=0.13

前端：aloam

![image-20250429085755633](./assets/image-20250429085755633.png)

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：RING++ icp threshold=0.15

前端：aloam

![image-20250429091151579](./assets/image-20250429091151579.png)

数据集：mr_slam提供的数据集loop_22.bag,loop_30.bag,loop_31.bag

回环：RING icp threshold=0.13

前端：aloam

![image-20250429090514180](./assets/image-20250429090514180.png)
