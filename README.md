# Octomap using T265 and D415
Procedure to produce Octomap using T265 & D415 and interface with Pixhawk
1) Follow the procedure in the following link to install SDK for T265 and D415

    https://github.com/IntelRealSense/librealsense

2) To link Pixhawk and T265 use Auterion package which acts as bridge, which provides odometry data. Follow the steps to install Auterion package from the below link

    https://github.com/Auterion/VIO
    
## How To Run Hardware

### Terminal 1:-
```bash
cd catkin_ws
source devel/setup.bash
roslaunch px4_realsense_bridge bridge_px4.launch
```

### Terminal 2:-
```bash
cd catkin_fastplanner/
source devel/setup.bash
roslaunch Fastplanner MappingDrone.launch 
```

### Note:-
In bridge_px4.launch:
It launches mavros px4.launch - binary installed in our pc/ edit launch file if source installed
then it also launches bridge.launch - contains necessary tf and launches t265 and d415 cameras

In MappingDrone.launch:
it contains pubcampose - maintains dynamic tf between map and base_link
also downsamples using pcl manager
Launches octomap server
and launches rviz - octomap, camera pointcloud, tf
### Mapping Demo:-

![](https://github.com/Garuda-IIITH-RRC/Octomap-using-T265-and-D415-/blob/main/t265_d415.gif)
