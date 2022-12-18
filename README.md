# Agilex-Scout-Mini-Gazebo-Navigation
ROS Navigation Stack with AgileX SCOUT-mini Gazebo Simulator

## Implementation of Autonomous Driving System with AgileX SCOUT-mini gazebo simulator

### **0. Install the Gazebo software**

Gazebo is a robot simulator. Gazebo simulates multiple robots in a 3D environments, with extensive dynamic interaction between objects.

**Gazebo Download Link** : [http://gazebosim.org](http://gazebosim.org/)

Download and install gazebo. You can go to the website : <http://gazebosim.org/install>

### **1. Installation**

1. **Development Environment ubuntu 20.04 + [ROS Noetic desktop full](http://wiki.ros.org/noetic/Installation/Ubuntu)**

2. **Build ROS packages for Scout simulator**

    * Create worksapce, download ROS packages

    ```
    mkdir -p ~/scout_ws/src
    cd ~/scout_ws/src
    git clone --recurse-submodules https://github.com/hjinnkim/Agilex-Scout-Mini-Gazebo-Navigation.git
    ```

3. **Install required ROS packages**

    ```(dependencies) and build from source
    cd Agilex-Scout-Mini-Gazebo-Navigation
    sh install_packages.sh
    ```
    Gmapping, Navigation, Robot_localization packages will be downloaded


4. **Install dependencies and build**

    ```
    cd ~/scout_ws
    rosdep install --from-paths src --ignore-src -r -y
    catkin_make
    ```
    **rosdep install** command will automatically install the required dependencies for the packages in the workspace. The dependencies are listed in CMakeLists.txt file in the packages.
### **2. Usage**

1. **Display platform description in RVIZ**
    ```
    cd ~/scout_ws
    source devel/setup.bash
    roslaunch scout_description display_scout_mini.launch 
    ```
    This will show you default vehicle platform without additional sensors.

2. **Launch gazebo simulator and teleop control**

    a. Launch gazebo simulator
    ```
    cd ~/scout_ws
    source devel/setup.bash
    roslaunch scout_gazebo_sim scout_mini_empty_world.launch
    ```

    b. Run teleop controller (move: w, a, x, d / stop: s)

    ```
    //Open another terminal

    cd ~/scout_ws
    source devel/setup.bash
    roslaunch scout_teleop scout_teleop_key.launch 
    ```

### **3. 2D SLAM**

Before running any command below, source devel/setup.bash

0. **Run Simulator**

    ```
    roslaunch scout_gazebo_sim scout_mini_playpen.launch
    ```

1. **Odometry & Kalman Filter Localization**
    ```
    roslaunch scout_base scout_mini_base.launch
    ```
    ```
    roslaunch scout_filter ekf_filter_cmd.launch
    ```

2. **SLAM mapping**

    a. Gmapping

    ```
    // Run gmapping slam
    roslaunch scout_slam scout_slam.launch
    ```

    b. Drive & mapping

    ```
    // Drive via teleop
    roslaunch scout_teleop scout_teleop_key.launch
    ```

    c. Save map

    ```
    // Save map
    roslaunch scout_slam gmapping_save.launch
    ```
    - default map file name: map1
    - map file will be saved in "scout_bringup/scout_slam/maps"
    - you can change saved map file name in the launch file
    - or you can set file name
        ```
        roslaunch scout_slam gmapping_save.launch map_file:=(file name)
        ```

### 3. **2D Navigation**

Before running any command below, source devel/setup.bash

0. **Run Simulator**

    ```
    roslaunch scout_gazebo_sim scout_mini_playpen.launch
    ```

1. **Odometry & Kalman Filter Localization**

    ```
    roslaunch scout_base scout_mini_base.launch
    ```

    ```
    roslaunch scout_filter ekf_filter_cmd.launch
    ```

2. Navigation

    ```
    // Run navigation
    roslaunch scout_navigation scout_navigation.launch
    ```
    you can set the destination via "2D Nav Goal" button

### Simulator Examples

<p align="center">
<img src="/resources/3d lidar.png" width=300px>
<br>
<img src="/resources/slam.png" width=300px>
<br>
<img src="/resources/planning.png" width=300px>
</p>

### Sensor settings

- Please refer [sensor directory](/sensor)

### References

- [agilexrobotics/scout_ros github repo](https://github.com/agilexrobotics/scout_ros)
- 