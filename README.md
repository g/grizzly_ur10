==============================
Usage with real Hardware
==============================

There are launch files available to bringup a real Grizzly + UR10 robot.

Don't forget to source the correct setup shell files and use a new terminal for each command!

To bring up the real robot, run:

roslaunch grizzly_ur10_bringup grizzly_ur10_bringup.launch robot_ip:=IP_OF_THE_ROBOT [reverse_port:=REVERSE_PORT]

A simple test script that moves the robot to predefined positions can be executed like this:

rosrun ur_driver test_move.py

CAUTION:
Remember that you should always have your hands on the big red button in case there is something in the way or anything unexpected happens.

==============================
MoveIt! with real Hardware
==============================

Additionally, you can use MoveIt! to control the robot.
There exist MoveIt! configuration packages for both robots.

For setting up the MoveIt! nodes to allow motion planning run:

roslaunch grizzly_ur10_moveit_config grizzly_ur10_moveit_planning_execution.launch

For starting up RViz with a configuration including the MoveIt! Motion Planning plugin run:

roslaunch grizzly_ur10_moveit_config moveit_rviz.launch config:=true

As MoveIt! seems to have difficulties with finding plans for the UR with full joint limits [-2pi, 2pi], there is a joint_limited version using joint limits restricted to [-pi,pi]. In order to use this joint limited version, simply use the launch file arguments 'limited', i.e.:

roslaunch grizzly_ur10_bringup grizzly_ur10_bringup.launch limited:=true robot_ip:=IP_OF_THE_ROBOT [reverse_port:=REVERSE_PORT]

roslaunch grizzly_ur10_moveit_config grizzly_ur10_moveit_planning_execution.launch limited:=true

roslaunch grizzly_ur10_moveit_config moveit_rviz.launch config:=true







===============================
Usage with Gazebo Simulation
===============================

There are launch files available to bringup a simulated robot.
In the following the commands for the UR5 are given. For the UR10, simply replace the prefix accordingly.

Don't forget to source the correct setup shell files and use a new terminal for each command!

To bring up the simulated robot in Gazebo, run:

roslaunch grizzly_ur10_gazebo grizzly_ur10.launch


===============================
MoveIt! with a simulated robot
===============================

Again, you can use MoveIt! to control the simulated robot.

For setting up the MoveIt! nodes to allow motion planning run:

roslaunch grizzly_ur10_moveit_config grizzly_ur10_moveit_planning_execution.launch sim:=true

For starting up RViz with a configuration including the MoveIt! Motion Planning plugin run:

roslaunch grizzly_ur10_moveit_config moveit_rviz.launch config:=true

NOTE:
As MoveIt! seems to have difficulties with finding plans for the UR with full joint limits [-2pi, 2pi], there is a joint_limited version using joint limits restricted to [-pi,pi]. In order to use this joint limited version, simply use the launch file arguments 'limited', i.e.:

roslaunch grizzly_ur10_gazebo grizzly_ur10.launch 

roslaunch grizzly_ur10_moveit_config grizzly_ur10_moveit_planning_execution.launch

roslaunch grizzly_ur10_moveit_config moveit_rviz.launch config:=true
