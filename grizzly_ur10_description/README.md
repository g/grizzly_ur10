UR10 Integration
================

UR10 is the preferred manipulation option for Grizzly. This package
contains a URDF description of Grizzly + UR10.


Usage
-----

If your Grizzly has a UR10, you can launch the additional driver
and MoveIt! components like so:

    roslaunch ur_bringup ur10_bringup.launch robot_ip:=192.168.1.19
    roslaunch ur10_moveit_config ur10_moveit_planning_execution.launch

If you'd like to run these always on startup, copy the two launchfiles
to `/etc/ros/hydro/grizzly-core.d`, where `robot_upstart` will pick them up.

To use the URDF, copy the `manipulator.urdf.xacro` file from the
`grizzly_ur10_description` package into `/etc/ros/hydro/grizzly-core.d`.
This will supplement the default one from `grizzly_description`, and
add the description for the manipulator.


Simulation
----------

To launch the integrated robot in simulation, run:

    roslaunch grizzly_gazebo description:=`rospack find grizzly_ur10_description`/urdf/base_with_manipulator.urdf.xacro

You will still need to separately run the MoveIt! configuration:

    roslaunch ur10_moveit_config ur10_moveit_planning_execution.launch


Visualization
-------------

When the full system (either real or simulated) is running, bring up
`rviz` to visualize the manipulator and robot together, using the launch
file provided by MoveIt:

    roslaunch ur10_moveit_config moveit_rviz.launch config:=true

