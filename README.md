# Robot-Path-Plannig-with-GWO-and-PSO-algorithms
This project uses Improved Grey Wolf Optimizer (IGWO) and Improved Particle Swarm Optimization (IPSO) for robot path planning with Laser Range Finder (LRF) data reduction in CoppeliaSim (V-REP). Robots autonomously navigate unknown environments and avoid collisions using IGWO/IPSO.  For a comprehensive understanding of the robot path planning methods used, including the laser range finder and novel objective functions in grey wolf optimization, refer to the paper: [Robot Path Planning Based on Laser Range Finder and Novel Objective Functions in Grey Wolf Optimizer](https://link.springer.com/article/10.1007/s42452-020-3093-5).

### CoppeliaSim Educational Version

The `.ttt` files included in this repository were created using the **Educational Version** of CoppeliaSim. These files contain simulation scenes and configurations designed for use with CoppeliaSim.

**Important:**

- **License Compliance**: The distribution and usage of these files are subject to the terms of the [CoppeliaSim Educational License](https://manual.coppeliarobotics.com/en/licensing.htm). Please review this license to ensure compliance.
- 
The `.ttt` files included in this repository were created using the **V-REP V3.5.0 Educational Version**. This project utilizes child scripts written in LUA programming language to implement the path-planning algorithms.

**Important:**

- **CoppeliaSim Transition**: V-REP has been discontinued and replaced by **CoppeliaSim**. CoppeliaSim is 100% compatible with V-REP, as it is a direct successor and fork of the V-REP project. It offers enhanced performance and additional features compared to V-REP. Support and licenses for V-REP are handled interchangeably with CoppeliaSim.

- **Tested Version**: This project has been tested with **CoppeliaSim V4.6.0**. Although initially developed in V-REP V3.5.0 Educational Version, the files are compatible with newer versions of CoppeliaSim.

- **Child Scripts for Independent Control**: Each robot in this simulation is controlled by a separate child script. This approach allows each robot to operate independently, with its own isolated state and path-planning algorithm. You can duplicate the robot model as needed, and each instance will execute its control script independently, facilitating a distributed multi-robot path planning setup.

- **Usage Instructions**: To use these `.ttt` files, download and install CoppeliaSim from the [official website](https://www.coppeliarobotics.com/). Open the files within CoppeliaSim to view and run the simulations.

- **Further Information**: For a comprehensive understanding of the robot path planning methods used, including the laser range finder and novel objective functions in grey wolf optimization, refer to the paper: [Robot Path Planning Based on Laser Range Finder and Novel Objective Functions in Grey Wolf Optimizer](https://link.springer.com/article/10.1007/s42452-020-3093-5).

# System Design and Multi-Robot Setup
In this project, we leverage CoppeliaSim's capability to handle multiple robots efficiently by utilizing child scripts. Each child script operates independently, with its own isolated state, allowing for effective distribution and management of tasks.
Typically, each robot is designed with its own navigation and path planning algorithm embedded within a child script. By attaching this script to a robot, you can then duplicate the robot as needed to create multiple independent robots. This approach ensures that each robot operates autonomously and according to its own script, facilitating scalable and flexible simulation scenarios.

## Problem Definition
The local path planning problem involves determining collision-free paths in an unknown environment. Each robot aims to navigate from an initial position to a final goal by finding safe positions step-by-step. This research utilizes relative localization, where each robot calculates its next position based on its current location, angle, and velocity within a given time period.

## Control Criteria and Rules
Predefined Positions: Each robot's initial and final positions are predefined.

Sensor-Based Detection: Robots use laser range finder sensors to detect their surrounding environment before making movements.

Movement Constraints: The maximum distance a robot can move in each step is determined by the sensor's radial detection range and the robot’s fixed velocity.

Stepwise Navigation: Path navigation from the start position to the goal is accomplished in multiple steps for each robot.

Direct Path to Goal: If the distance between the current position and the goal is within the sensor's detection area and no obstacles are present, the robot will move directly to the goal.

## Robot Path Planning Stages
This research addresses the distributed multi-robot path planning problem through three distinct stages, each operating individually for each robot:

Environment Sensing: The laser range finder (LRF) sensor, mounted on top of each robot, senses the environment within its range. This sensing occurs once per step before the robot begins to move.

Algorithm Processing: The robot’s current position and sensor data are used as inputs for the IGWO (Improved Grey Wolf Optimizer) or IPSO (Improved Particle Swarm Optimization) algorithms. A multi-objective function is employed in these algorithms to evaluate candidate solutions and guide convergence towards an optimal path.

Movement and Update: The robot moves to the best position identified by the algorithms. Its current position is then updated. This process is repeated until the robot successfully reaches its goal position.

# Project Overview

## CoppeliaSim Installation and Model Integration

### Installing CoppeliaSim

1. **Download CoppeliaSim**: Visit the [official CoppeliaSim website](https://www.coppeliarobotics.com/) and download the latest version of CoppeliaSim. Note that the project has been tested with **CoppeliaSim V4.6.0**.

2. **Install CoppeliaSim**: Follow the installation instructions provided on the website to install CoppeliaSim on your computer.

3. **Open CoppeliaSim**: After installation, launch CoppeliaSim.

### Adding the Khepera IV Model

1. **Download Khepera IV Model**: Obtain the Khepera IV model file (`KheperaIV.ttm`) from the GitHub repository: [KheperaIV.ttm](https://github.com/EAPH/K4_Model_VREP).

2. **Copy Model File**:
   - Navigate to your CoppeliaSim installation directory.
   - Locate the folder: `..\CoppeliaRobotics\CoppeliaSimEdu\models\robots\mobile`.
   - Copy the `Khepera-IV.ttm` file into this folder.

3. **Verify Integration**:
   - Restart CoppeliaSim if it was open during the copy process.
   - Open CoppeliaSim and go to the model selection menu.
   - You should now see the Khepera IV model listed among the available models.

### Using the `.ttt` Files

1. **Open Simulation Files**:
   - Download the `.ttt` files from this repository.
   - Open these files within CoppeliaSim to view and run the simulations.

2. **Run Simulations**:
   - Configure any necessary settings or parameters in CoppeliaSim.
   - Start the simulation to see the path planning in action.

By following these steps, you can set up your environment and integrate the Khepera IV model for your simulations.

For further details on the path-planning methods used and additional information, refer to the project documentation and relevant research papers.


<p align="center">
  <img src="images/Scene1IGWO.PNG" width="30%" />
  <img src="images/Scene1IGWO.PNG" width="30%" />
  <img src="images/Scene1IGWO.PNG" width="30%" />
</p>
