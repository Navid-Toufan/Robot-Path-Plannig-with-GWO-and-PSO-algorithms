# Robot-Path-Plannig-with-GWO-and-PSO-algorithms
This project uses Improved Grey Wolf Optimizer (IGWO) and Improved Particle Swarm Optimization (IPSO) for robot path planning with Laser Range Finder (LRF) data reduction in CoppeliaSim (V-REP). Robots autonomously navigate unknown environments and avoid collisions using IGWO/IPSO.  For a comprehensive understanding of the robot path planning methods used, including the laser range finder and novel objective functions in grey wolf optimization, refer to the paper: [Robot Path Planning Based on Laser Range Finder and Novel Objective Functions in Grey Wolf Optimizer](https://link.springer.com/article/10.1007/s42452-020-3093-5).

### CoppeliaSim Educational Version

The `.ttt` files included in this repository were created using the **V-REP V3.5.0 Educational Version**. This project utilizes child scripts written in LUA programming language to implement the path-planning algorithms.

**Important:**

- **CoppeliaSim Transition**: V-REP has been discontinued and replaced by **CoppeliaSim**. CoppeliaSim is 100% compatible with V-REP, as it is a direct successor and fork of the V-REP project. It offers enhanced performance and additional features compared to V-REP. Support and licenses for V-REP are handled interchangeably with CoppeliaSim.

- **Tested Version**: This project has been tested with **CoppeliaSim V4.6.0**. Although initially developed in V-REP V3.5.0 Educational Version, the files are compatible with newer versions of CoppeliaSim.

- **License Compliance**: The distribution and usage of these files are subject to the terms of the [CoppeliaSim Educational License](https://www.coppeliarobotics.com/helpFiles/en/eduLicense.htm). Please review this license to ensure compliance.

- **Khepera IV Model**: This project utilizes the Khepera IV model, a mobile robot, for simulation purposes. To integrate the Khepera IV model with CoppeliaSim, follow these steps:
  
  1. Download the Khepera IV model file from the GitHub repository: [KheperaIV.ttm](https://github.com/EAPH/K4_Model_VREP).
  2. Copy the downloaded file to the following path in your CoppeliaSim installation directory: `..\V-REP3\V-REP_PRO_EDU\models\robots\mobile`.
  3. Once copied, the Khepera IV model will appear in the list of models within CoppeliaSim.

- **Usage Instructions**: To use these `.ttt` files, download and install CoppeliaSim from the [official website](https://www.coppeliarobotics.com/). Open the files within CoppeliaSim to view and run the simulations.

- **Further Information**: For a comprehensive understanding of the robot path planning methods used, including the laser range finder and novel objective functions in grey wolf optimization, refer to the paper: [Robot Path Planning Based on Laser Range Finder and Novel Objective Functions in Grey Wolf Optimizer](https://link.springer.com/article/10.1007/s42452-020-3093-5).

# System Design and Multi-Robot Setup
In this project, we leverage CoppeliaSim's capability to handle multiple robots efficiently by utilizing child scripts. Each child script operates independently, with its own isolated state, allowing for effective distribution and management of tasks.
Typically, each robot is designed with its own navigation and path planning algorithm embedded within a child script. By attaching this script to a robot, you can then duplicate the robot as needed to create multiple independent robots. This approach ensures that each robot operates autonomously and according to its own script, facilitating scalable and flexible simulation scenarios.

# Problem Definition
The local path planning problem involves determining collision-free paths in an unknown environment. Each robot aims to navigate from an initial position to a final goal by finding safe positions step-by-step. This research utilizes relative localization, where each robot calculates its next position based on its current location, angle, and velocity within a given time period.

# Control Criteria and Rules
Predefined Positions: Each robot's initial and final positions are predefined.

Sensor-Based Detection: Robots use laser range finder sensors to detect their surrounding environment before making movements.

Movement Constraints: The maximum distance a robot can move in each step is determined by the sensor's radial detection range and the robot’s fixed velocity.

Stepwise Navigation: Path navigation from the start position to the goal is accomplished in multiple steps for each robot.

Direct Path to Goal: If the distance between the current position and the goal is within the sensor's detection area and no obstacles are present, the robot will move directly to the goal.

# Robot Path Planning Stages
This research addresses the distributed multi-robot path planning problem through three distinct stages, each operating individually for each robot:

Environment Sensing: The laser range finder (LRF) sensor, mounted on top of each robot, senses the environment within its range. This sensing occurs once per step before the robot begins to move.

Algorithm Processing: The robot’s current position and sensor data are used as inputs for the IGWO (Improved Grey Wolf Optimizer) or IPSO (Improved Particle Swarm Optimization) algorithms. A multi-objective function is employed in these algorithms to evaluate candidate solutions and guide convergence towards an optimal path.

Movement and Update: The robot moves to the best position identified by the algorithms. Its current position is then updated. This process is repeated until the robot successfully reaches its goal position.
