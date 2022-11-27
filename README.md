# Agilex-Scout-Mini-Gazebo-Navigation
ROS Navigation Stack with AgileX SCOUT-mini Gazebo Simulator

## Implementation of Autonomous Driving System with AgileX SCOUT-mini gazebo simulator

### **0. Install the Gazebo software**

Gazebo is a robot simulator. Gazebo simulates multiple robots in a 3D environments, with extensive dynamic interaction between objects.

**Gazebo Download Link** : [http://gazebosim.org](http://gazebosim.org/)

Download and install gazebo. You can go to the website : <http://gazebosim.org/install>

### **1. Installation**

1. **development Environment ubuntu 20.04 + [ROS Noetic desktop full](http://wiki.ros.org/noetic/Installation/Ubuntu)**

2. **Build ROS packages for Scout simulator**

    * Create worksapce, download ROS packages

    ```
    mkdir -p ~/scout_ws/src
    cd ~/scout_ws/src
    git clone --recurse-submodules https://github.com/hjinnkim/BTS_scout_mini.git
    ```

3. **Install required ROS packages**

    a. Noetic

    ```(dependencies) and build from source
    cd BTS_scout_mini
    sh install_dependencies_noetic.sh
    ```


4. **Install dependencies and build**

    ```
    cd ~/udf
    rosdep install --from-paths src --ignore-src -r -y
    catkin_make

### **2. Usage**
    ```
    cd ~/scout_ws
    source devel/setup.bash
    roslaunch scout_description display_scout_mini.launch 
    ```

2. **Launch gazebo simulator and teleop control**u

    a. Launch gazebo simulator

    ```uu
    cd ~/scout_ws
    source devel/setup.bash
    roslaunch scout_gazebo_sim scout_mini_playpen.launch
    ```

    b. Run teleop controller (w, a, s, d)

    ```
    //Open another terminal

    cd ~/scout_ws
    roslaunch scout_teleop scout_teleop_key.launch 
    ```

### **3. 2D Navigation**

1. **SLAM mapping**

    a. Gmapping

    ```
    // Run gmapping slam

    roslaunch scout_slam scout_slam.launch
    ```

    ```
    // Save map (Another terminal)

    roslaunch scout_slam gmapping_save.launch
    ```

    b. Cartographer

    To be added

2. **Navigation**

    ```
    // Run navigation

    roslaunch scout_navigation scout_navigation.launch
    ```

### **4. 3D navigation**

To be added
