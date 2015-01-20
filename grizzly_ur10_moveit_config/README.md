================ To close the gripper in simulation  =============================
Make sure the Gazebo simulation of the Grizzly UR10 is up and running before calling this command.

If it's not, you may start it by (first make sure your workspace is sourced to devel/setup.bash if it is installed by source, or /opt/ros/${rosdistro}/setup.bash if from apt-get)

    roslaunch grizzly_ur10_gazebo grizzly_ur10.launch

This command will open the gripper:  

    rostopic pub --oleft_hand/command robotiq_s_model_articulated_msgs/SModelRobotOutput {1,2,1,0,0,0,0,255,0,155,0,0,255,0,0,0,0,0}

This command will close the gripper: 

    rostopic pub --once left_hand/command robotiq_s_model_articulated_msgs/SModelRobotOutput {1,1,1,0,0,0,255,255,0,155,0,0,255,0,0,0,0,0}

================ To move the arm in simulation ===================================

Have the Gazebo simulation up and running: 

    roslaunch grizzly_ur10_gazebo grizzly_ur10.launch

Start the trajectory execution for simulation. This will allow the controllers to move the robot and bring up move_group which accepts PlanningRequest messages.

    roslaunch grizzly_ur10_moveit_config grizzly_ur10_planning_execution.launch sim:=true

Start RViz which will provide an interface to move around the arm.

    roslaunch grizzly_ur10_moveit_config moveit_rviz.launch config:=true

Make sure you set the planning request to be: ur10_arm so you can control the arm. It will also have interactive markers around it. hit the "Plan and execute" button once you have selected a nice location for the arm, and by nice it means a place where there is no red. 


