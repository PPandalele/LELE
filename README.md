# Project Overview  
This project implements an autonomous pick-and-place system using a UR5e robotic arm equipped with a Robotiq 85 gripper to manipulate golf balls in a Gazebo simulation environment. The system utilizes ROS2 Humble, MoveIt motion planning, and precise trajectory control to achieve reliable object manipulation.

# Project Structure 
ur5e_gripper_moveit_config/
├── config/                          # Configuration files 
│   ├── ur5e_gripper_controllers.yaml   # Controller parameters 
│   ├── joint_limits.yaml               # Joint constraints 
│   ├── kinematics.yaml                 # Kinematics solver 
│   ├── ompl_planning.yaml              # Motion planners 
│   └── initial_positions.yaml          # Initial robot pose 
├── launch/                          # Launch files
│   ├── golf_ball_pick_place.launch.py  # Main launch script 
│   └── golf_ball_controller.py         # Control logic 
├── urdf/                            # Robot descriptions 
│   ├── ur5e_gripper.urdf.xacro         # Robot URDF 
│   └── golf_ball.urdf                  # Object URDF 
├── worlds/                          # Simulation environments 
│   └── golf_ball_word.world            # Gazebo world 
├── srdf/                            # Semantic descriptions 
│   └── ur5e_gripper.srdf.xacro         # Robot SRDF 
└── rviz/                            # Visualization 
    └── view_robot.rviz                  # RViz configuration 
# Launch
ros2 launch ur5e_gripper_moveit_config golf_ball_pick_place.launch.py

⚠️ Critical Issue: Inaccurate Golf Ball Grasping 
Problem Description：
The current system experiences difficulty in accurately grasping golf balls due to several technical challenges encountered during development:
Coordinate Frame Misalignment: Discrepancy between ball spawn position and robot reach coordinates
Trajectory Tolerance Violations: Joint position errors exceeding controller limits (±0.2 rad)
Self-Collision During Motion: Upper arm link colliding with base during complex trajectories
Workspace Constraint Conflicts: Table collision avoidance interfering with precise positioning
