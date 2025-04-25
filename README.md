# ANSASV: Autonomous Navigation Stack for Autonomous Surface Vehicles

ANSASV is an open-source, modular ROS2-based framework for autonomous surface vehicle (ASV) navigation, supporting waypoint-based navigation, dynamic obstacle avoidance, waterbody awareness, and modular mission planning. This project is designed to enable autonomous marine applications like patrolling, ocean/lake cleaning, bathymetry mapping, and sample collection, with an emphasis on flexibility, real-time awareness, and scalability.

---

## Table of Contents
1. [Motivation](#motivation)
2. [What's the Idea?](#whats-the-idea)
3. [Approach](#approach)
4. [Use Cases](#use-cases)
5. [Milestones](#milestones)
6. [Contributing](#contributing)
7. [Open Questions](#open-questions)

---

## Motivation: Why This Project?

Autonomous Surface Vehicles (ASVs) are essential for numerous real-world applications such as:
- Waterbody surveillance
- Environmental monitoring
- Ocean cleaning
- Bathymetric surveying
- Search & rescue

However, there is a lack of open-source, modular frameworks to support the development of autonomous navigation systems for surface vessels. ANSASV aims to fill this gap by providing:
- A modular, easy-to-extend navigation stack based on ROS2.
- An interactive UI to define tasks like waypoint navigation, surveying, and patrolling.
- A real-time environmental awareness system (e.g., detecting shorelines, obstacles, and depth awareness).

---

## What's the Idea?

The goal of **ANSASV** is to build a flexible and modular framework for Autonomous Surface Vehicles (ASVs) that can:
- Navigate via waypoints based on user input from a web-based UI (Google Maps-like interface).
- Be used for various marine tasks: patrolling, ocean/lake cleaning, bathymetric mapping, sample collection.
- Support real-time awareness of the vehicle’s surroundings, including:
  - **Water vs. Land Awareness**
  - **Shoreline detection**
  - **Dynamic obstacle avoidance** using sensors like LIDAR
  - **Depth awareness** for avoiding shallow waters
- Generate GPS waypoints from user-defined tasks and convert them into executable plans.

This project allows easy modularization, where you can swap or extend features based on specific use cases while keeping autonomous navigation as the core.

---

## Approach

We will achieve this by combining **ROS2** with the following key components:

### 1. Simulation Setup:
- Use **Gazebo** with the **WAM-V** model or a custom surface vessel.
- Sensors: **GPS**, **LIDAR**, **IMU**, and **depth sensors**.
- **Costmap**: Build local costmap with LIDAR and shore detection.
- **Map Server**: Serve a global waterbody boundary (GeoJSON format).

### 2. Waypoint-Based Navigation:
- Mission Planner converts user commands (e.g., survey a lake) into waypoints.
- **Waypoint Follower** executes these waypoints using the vehicle's control systems.

### 3. Behavior Tree (BT):
- A modular **Behavior Tree** (using Behavior Tree.CPP) to define missions (patrolling, cleaning, mapping, etc.).
- This allows easy task execution logic that can be customized for different missions.

### 4. Dynamic Environment Awareness:
- **Shoreline Detection**: Vehicle identifies if it's getting close to land or shallow waters.
- **Obstacle Avoidance**: Real-time obstacle detection using LIDAR and costmaps.
- **Water Awareness**: Real-time waterbody boundary detection, depth-aware decision-making.

### 5. UI Interface:
- Web-based interface to draw waterbody boundaries and define tasks.
- Displays the vehicle’s position on a Google Maps-like interface.

---

## Use Cases

This modular framework can be extended to perform multiple types of autonomous marine tasks, including:
- **Patrolling vehicle** for waterbody surveillance.
- **Ocean/Lake cleaner** for cleaning debris or waste.
- **Bathymetry mapper** for ocean/lake floor mapping.
- **Sample collector** for environmental sample collection.

---

## Milestones

1. **Simulation Environment Setup:**
   - Initialize Gazebo simulation with a custom or WAM-V model.
   - Configure sensors (GPS, LIDAR, IMU, etc.).
   - Create a costmap for local and global navigation.

2. **Waypoint Navigation:**
   - Implement basic waypoint navigation.
   - Integrate Mission Planner and Waypoint Follower modules.

3. **Obstacle Avoidance:**
   - Implement dynamic obstacle avoidance using LIDAR data.

4. **Behavior Tree Integration:**
   - Build and integrate a modular behavior tree for mission handling (e.g., patrolling, cleaning).

5. **UI Development:**
   - Implement a web-based interface to set waypoints and display vehicle status.

6. **Depth Awareness & Shoreline Detection:**
   - Develop systems for detecting shallow waters and shorelines to avoid land.

7. **Testing and Real-World Deployment:**
   - Conduct simulations and deploy to real hardware (WAM-V or similar).

---

## Contributing

We want to make ANSASV as accessible and community-driven as possible! You can contribute in the following ways:

### 1. Code Contributions:
- Fork the repo and submit a pull request.
- Fix bugs, add new features, or enhance existing modules.

### 2. Open Issues:
- Report bugs or suggest improvements through GitHub Issues.
- Suggest new features or missions for the vehicle.

### 3. Participate in Discussions:
- Engage in GitHub Discussions for ideas, issues, and design questions.
- Ask about improvements or share new ideas for the framework.

---

## Open Questions (Help Needed)

We’re looking for feedback and suggestions from the community. Please help answer or discuss the following questions:

### General Design Questions:
1. How should we define the geofencing system for waterbodies?
   - Should it be a preloaded map or a dynamic system that detects shorelines in real-time?

2. How can we simulate water depth changes or coastal terrain realistically in Gazebo?
   - Are there any existing tools that can assist with bathymetry or terrain profiling?

### Navigation and Awareness:
1. How can we improve the way the vehicle detects the shoreline or land boundaries dynamically?
2. Should we rely solely on GPS or combine it with additional sensing technologies like sonar?
3. What’s the best way to incorporate depth-awareness in waypoint navigation?
4. Should the vehicle dynamically adjust its path if it senses shallow waters?

### Behavior Trees and Mission Control:
1. What’s the ideal Behavior Tree design for a marine vehicle to handle multi-stage missions?
2. Should we focus on simple tasks or allow complex, hierarchical mission designs?

### UI and User Input:
1. How can we design a user interface to define tasks like surveying or patrolling in a simple, intuitive way?
2. What kind of visual feedback should be shown to the user during the mission execution?
