gundam_robot_Panama
========================================================================================================================================================================
ROS packages for GUNDAM robots

original: https://github.com/gundam-global-challenge/gundam_robot.git


![GUNDAM Gazebo Simulation](imgs/gundam_AKG.jpg)



How to setup workspace
----------------------

```
$ mkdir -p catkin_ws/src
$ cd  catkin_ws
$ cd src/
$ git clone https://github.com/GenteBuena/gundam_robot_panama.git
$ cd ..
$ source /opt/ros/$ROS_DISTRO/setup.bash
$ rosdep install -y -r --from-paths src --ignore-src
$ catkin_make
$ source devel/setup.bash
```

Visualize URDF model
===========================

URDF file in rviz, you can use `display.launch` file.
```
$ roslaunch gundam_rx78_description display.launch
```

![Rviz](imgs/rviz.png)


![Rviz](imgs/rviz.gif)

Map of Panamá
===========================

![Rviz](imgs/mapPanama.png)







Run gazebo simulation
============================

To run a gazebo simulation

```
$ roslaunch gundam_rx78_gazebo gundam_rx78_world.launch
```

To control joint angles
------------

You can run "Robot"-like walking pattern on simulation

```
$ roslaunch gundam_rx78_gazebo gundam_rx78_walk.launch
```

```
# step
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/step.csv
# walk forward
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-forward.csv
# walk backward
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-backward.csv
# walk to right
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-to-right.csv
# walk to left
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-to-left.csv
# turn right
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/turn-right.csv
# turn left
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/turn-left.csv
```

```
# raise Arms and walk
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/up.csv
```

![Simulation](imgs/gundamAKG.gif)

Note that currently, we have several limitation on this simulation, we only have position controller etc.

You can also find sample motion control files in the `gundam_rx78_control/sample` directory.

joint_trajectory_client_csv.py
----------------------

using the gundam control with joint_tajectory_client_csv.py and inputting a .csv file 

This will use the patterns indicated in the file to simulate the movement of the gundam according to the values of the angles of each component.


video Youtube: 
----------------------

https://www.youtube.com/watch?v=n6lPjfBhPsI&feature=emb_logo