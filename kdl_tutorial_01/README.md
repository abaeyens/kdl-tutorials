# KDL tutorial 01: URDF + IK

In this tutorial/blogpost, we will go through setting up KDL in ROS2,
constructing the KDL kinematic tree from the `/robot_description` topic
(i.e. using URDF), and solving an inverse kinematics case.

Subjects:
- construct `KDL::Tree` from URDF broadcast on `/robot_description` topic
- extract kinematic chains of interest from tree
- set up IK solver
- run IK solver

## Build and run
```bash
colcon build
source install/setup.bash
ros2 launch kdl_tutorial_01 app.launch.xml
```

Example output:
```
$ ros2 launch kdl_tutorial_01 app.launch.xml
[INFO] [launch]: All log files can be found below /home/user/.ros/log/2024-04-27-17-17-53-981238-nest-1664
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [main-1]: process started with pid [1668]
[INFO] [robot_state_publisher-2]: process started with pid [1670]
[robot_state_publisher-2] [INFO] [1714238274.309565995] [robot_state_publisher]: got segment base_link
[robot_state_publisher-2] [INFO] [1714238274.309715872] [robot_state_publisher]: got segment foot
[robot_state_publisher-2] [INFO] [1714238274.309725073] [robot_state_publisher]: got segment lower_leg
[robot_state_publisher-2] [INFO] [1714238274.309745704] [robot_state_publisher]: got segment upper_leg
[main-1] nb joints:        2
[main-1] nb segments:      3
[main-1] root segment:     base_link
[main-1] chain nb joints:  2
[main-1] knee and hip joint angles: -74.4, 95.7 °
```
