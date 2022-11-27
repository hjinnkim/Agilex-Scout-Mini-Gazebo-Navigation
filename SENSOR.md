## **Sensors**
### Add LiDAR
#### Reference

* https://www.youtube.com/watch?v=jJzzw2jk-lY

* https://classic.gazebosim.org/tutorials?tut=ros_gzplugins#GPULaser

* https://level-asphalt-6c6.notion.site/Gazebo-Scout-mini-add-lidar-086c23578e904467864f284ad02c8564

* hokuyo.dae : https://github.com/osrf/gazebo_models/tree/master/hokuyo/meshes

#### How to change lidar range
* You can change lidar range by editing parameters in **ugv_gazebo_sim/scout/scout_description/urdf/mini.xacro**

    ![img](images/lidar_range.png)

    By editing parameters in min, max part, you can change lidar range

### Add realsense camera
#### Reference

* https://github.com/pal-robotics/realsense_gazebo_plugin

* https://github.com/pal-robotics/realsense_gazebo_plugin/issues/7

* https://github.com/IntelRealSense/realsense-ros

* urdf : https://github.com/IntelRealSense/realsense-ros/tree/development/realsense2_description/urdf

* d435.dae : https://github.com/IntelRealSense/realsense-ros/tree/development/realsense2_description/meshes

#### If compressed image topics are not published
* try to install following ros packages where < distribution> is your ros-distro
    ```
    sudo apt install ros-<distribution>-image-transport-plugins ros-<distribution>-compressed-image-transport ros-<distribution>-theora-image-transport ros-<distribution>-compressed-depth-image-transport
    ```

### Add IMU sensor
#### Reference

https://classic.gazebosim.org/tutorials?tut=ros_gzplugins#IMU(GazeboRosImu)

https://answers.ros.org/question/12430/modelling-sensorsimu-in-gazebo/

