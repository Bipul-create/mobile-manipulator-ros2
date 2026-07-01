# ROS2 Mobile Manipulator Simulation 

Hi! I built this project as my final capstone for Edouard Renard's **ROS2 for Beginners (Level 2)** course. It is a simulation of a Mobile Manipulator (a differential drive mobile base integrated with a multi-DOF robotic arm) fully configured and controlled in ROS2.

The goal of this project was to learn modular robot modeling using URDF/Xacro and orchestrate simulation layers using launch files.

---

##  Simulation Preview

<img width="1372" height="852" alt="image" src="https://github.com/user-attachments/assets/f723ac1a-0d98-4231-8b5c-be1c9e95a844" />


---

##  What I Learned & Implemented

* **Modular Robot Modeling (Xacro Macros):** Instead of writing one giant URDF file, I broke down the robot components into modular macros inside my_robot_description/urdf/:
  * 'mobile_base.xacro' & 'arm.xacro' for the core links and joints.
  * 'camera.xacro' for sensor integration.
  * 'common_properties.xacro' for materials and physics parameters.
  * Gazebo-specific extensions ('arm_gazebo.xacro', 'mobile_base_gazebo.xacro') for future simulation physics.
* **Launch Orchestration:** Configured standard ROS2 launch setups to parse the Xacro tree and publish robot states cleanly.
* **Coordinate Transforms ($TF$ Tree):** Verified the dynamic transformation tree and physical limits inside RViz2 using the joint state setups.

---

##  Repository Structure

Based on the workspace layout, here is how the files are structured inside the 'my_robot' package:


my_robot/
├── my_robot_bringup/
│   └── launch/
│       └── my_robot_gazebo.launch.xml   # Simulation launch file
├── my_robot_description/
│   ├── rviz/
│   │   └── urdf_config.rviz             # Pre-saved RViz layout
│   └── urdf/
│       ├── arm.xacro
│       ├── arm_gazebo.xacro
│       ├── camera.xacro
│       ├── common_properties.xacro
│       ├── mobile_base.xacro
│       ├── mobile_base_gazebo.xacro
│       ├── my_robot.urdf.xacro          # Main top-level xacro file
│       └── standalone_arm.urdf.xacro
├── CMakeLists.txt                       # Build configuration
├── my_rviz_pic.jpeg                     # Workspace Preview Image
├── package.xml.xml                      # Dependencies manifest
└── README.md
