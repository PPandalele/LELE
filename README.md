# Project Overview  
This project implements an autonomous pick-and-place system using a UR5e robotic arm equipped with a Robotiq 85 gripper to manipulate golf balls in a Gazebo simulation environment. The system utilizes ROS2 Humble, MoveIt motion planning, and precise trajectory control to achieve reliable object manipulation.

# Project Structure 
ur5e_gripper_moveit_config/
├── config/                          
│   ├── ur5e_gripper_controllers.yaml   
│   ├── joint_limits.yaml              
│   ├── kinematics.yaml                
│   ├── ompl_planning.yaml              
│   └── initial_positions.yaml          
├── launch/                          
│   ├── golf_ball_pick_place.launch.py  
│   └── golf_ball_controller.py         
├── urdf/                            
│   ├── ur5e_gripper.urdf.xacro         
│   └── golf_ball.urdf                  
├── worlds/                          
│   └── golf_ball_word.world            
├── srdf/                            
│   └── ur5e_gripper.srdf.xacro         
└── rviz/                            
    └── view_robot.rviz                
# Launch
ros2 launch ur5e_gripper_moveit_config golf_ball_pick_place.launch.py

# Probelm
⚠️ Critical Issue: Inaccurate Golf Ball Grasping 
Problem Description：
The current system experiences difficulty in accurately grasping golf balls due to several technical challenges encountered during development:
Coordinate Frame Misalignment: Discrepancy between ball spawn position and robot reach coordinates
Trajectory Tolerance Violations: Joint position errors exceeding controller limits (±0.2 rad)
Self-Collision During Motion: Upper arm link colliding with base during complex trajectories
Workspace Constraint Conflicts: Table collision avoidance interfering with precise positioning
