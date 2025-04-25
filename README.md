# ANSASV: Autonomous Navigation Stack for Autonomous Surface Vehicles

ANSASV is an open-source, modular ROS2-based framework for autonomous surface vehicle (ASV) navigation, supporting waypoint-based navigation, dynamic obstacle avoidance, waterbody awareness, and modular mission planning. This project is designed to enable autonomous marine applications like patrolling, ocean/lake cleaning, bathymetry mapping, and sample collection, with an emphasis on flexibility, real-time awareness, and scalability.


---

Table of Contents

1. Motivation


2. What's the Idea?


3. Approach


4. Use Cases


5. Milestones


6. Contributing


7. Open Questions




---

Motivation: Why This Project?

Autonomous Surface Vehicles (ASVs) are essential for numerous real-world applications such as:

Waterbody surveillance

Environmental monitoring

Ocean cleaning

Bathymetric surveying

Search & rescue


However, there is a lack of open-source, modular frameworks to support the development of autonomous navigation systems for surface vessels. ANSASV aims to fill this gap by providing:

A modular, easy-to-extend navigation stack based on ROS2.

An interactive UI to define tasks like waypoint navigation, surveying, and patrolling.

A real-time environmental awareness system (e.g., detecting shorelines, obstacles, and depth awareness).



---

What's the Idea?

The goal of ANSASV is to build a flexible and modular framework for Autonomous Surface Vehicles (ASVs) that can:

Navigate via waypoints based on user input from a web-based UI (Google Maps-like interface)

Be used for various marine tasks: patrolling, ocean/lake cleaning, bathymetric mapping, sample collection

Support real-time awareness of the vehicle’s surroundings, including:

Water vs. Land Awareness

Shoreline detection

Dynamic obstacle avoidance using sensors like LIDAR

Depth awareness for avoiding shallow waters


Generate GPS waypoints from user-defined tasks and convert them into executable plans


This project allows easy modularization, where you can swap or extend features based on specific use cases while keeping autonomous navigation as the core.


---

Approach

We will achieve this by combining ROS2 with the following key components:

1. Simulation Setup:

Use Gazebo with the WAM-V model or a custom surface vessel

Sensors: GPS, LIDAR, IMU, and depth sensors

Costmap: Build local costmap with LIDAR and shore detection

Map Server: Serve a global waterbody boundary (GeoJSON format)



2. Waypoint-Based Navigation:

Mission Planner converts user commands (e.g., survey a lake) into waypoints

Waypoint Follower executes these waypoints using the vehicle's control systems



3. Behavior Tree (BT):

A modular Behavior Tree (using Behavior Tree.CPP) to define missions (patrolling, cleaning, mapping, etc.)

This allows easy task execution logic that can be customized for different missions



4. Dynamic Environment Awareness:

Shoreline Detection: Vehicle identifies if it's getting close to land or shallow waters

Obstacle Avoidance: Real-time obstacle detection using LIDAR and costmaps

Water Awareness: Real-time waterbody boundary detection, depth-aware decision-making



5. UI Interface:

Web-based interface to draw waterbody boundaries and define tasks.

Displays the vehicle’s position on a Google Maps-like interface.





---

Use Cases

This modular framework can be extended to perform multiple types of autonomous marine tasks, including:


---

Milestones


---

Contributing

We want to make ANSASV as accessible and community-driven as possible! You can contribute in the following ways:

1. Code Contributions:

Fork the repo and submit a pull request

Fix bugs, add new features, or enhance existing modules


2. Open Issues:

Report bugs or suggest improvements through GitHub Issues

Suggest new features or missions for the vehicle


3. Participate in Discussions:

Engage in GitHub Discussions for ideas, issues, and design questions

Ask about improvements or share new ideas for the framework



---

Open Questions (Help Needed)

We’re looking for feedback and suggestions from the community. Please help answer or discuss the following questions:

General Design Questions:

How should we define the geofencing system for waterbodies?

Should it be a preloaded map or a dynamic system that detects shorelines in real-time?


How can we simulate water depth changes or coastal terrain realistically in Gazebo?

Are there any existing tools that can assist with bathymetry or terrain profiling?



Navigation and Awareness:

How can we improve the way the vehicle detects the shoreline or land boundaries dynamically?

Should we rely solely on GPS or combine with additional sensing technologies like sonar?


What’s the best way to incorporate depth-awareness in waypoint navigation?

Should the vehicle dynamically adjust its path if it senses shallow waters?



Behavior Trees and Mission Control:

What’s the ideal Behavior Tree design for a marine vehicle to handle multi-stage missions?

Should we focus on simple tasks or allow complex, hierarchical mission designs?



UI and User Input:

How can we design a user interface to define tasks like surveying or patrolling in a simple, intuitive way?

What kind of visual feedback should be shown to the user during the mission execution?




---

How to Get Started

1. Clone the repository:

git clone https://github.com/<your-username>/ANSASV.git


2. Set up dependencies and environment:

cd ANSASV
source install/setup.bash


3. Run the basic simulation:

ros2 launch ansasv_launch simulation.launch.py


4. Check out docs/architecture.md for an in-depth overview of the project structure and component details.




---

Repository Structure

ANSASV/
├── README.md
├── docs/
│   ├── architecture.md
│   ├── sensor_config.md
│   ├── behavior_tree.md
│   └── demo_scenarios.md
├── launch/
│   └── simulation.launch.py
├── config/
│   └── wmv_config.yaml
├── src/
│   ├── map_server/
│   ├── depth_checker/
│   ├── costmap_updater/
│   ├── bt_navigator/
│   ├── waypoint_follower/
│   └── ui_interface/
├── worlds/
│   └── lake_sim.world
├── assets/
│   └── waterbody.geojson
└── Dockerfile


---

With this setup, contributors can easily dive in, and we’ll have clear guidance on what questions we need expert feedback on. Would you like me to help create the initial GitHub repo structure based on this, so it's ready for contributors?

