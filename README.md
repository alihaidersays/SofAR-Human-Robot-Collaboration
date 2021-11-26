# Human-Baxter Collaboration

## Software Architecture for Robotics | Group: HRC-07
1. Syed Hasan Shozab Abidi, _[4929631@studenti.unige.it](mailto:4929631@studenti.unige.it)_
2. Muhammad Ali Haider Dar, _[5046263@studenti.unige.it](mailto:5046263@studenti.unige.it)_
3. Soundarya Pallanti, _[4807289@studenti.unige.it](mailto:4807289@studenti.unige.it)_
4. Abhilash Jakkampudi, _[5058208@studenti.unige.it](mailto:5058208@studenti.unige.it)_

MSc Robotics Engineering, University of Genoa, Italy

Instructor: Prof. [Fulvio Mastrogiovanni](https://rubrica.unige.it/personale/UkNHWFhr)

### Unity Installation (Windows)

Visit [Unity website](https://unity3d.com/get-unity/download) and download Unity Hub
Through the Hub, install Unity 2020.2.2 (the version for which the projects have been developed) or later. Beware that later versions (eg. Unity 2021.1.x) may be incompatible with the projects

### ROS Version
ROS Noetic version was used for this project.

### Installation and Setup

#### 1. On Ubuntu
* Download ROS packages required for this project from the [main repository](https://github.com/TheEngineRoom-UniGe/SofAR-Human-Robot-Collaboration).
* Extract the packages to your catkin_ws. 
* Replace the 'human_baxter_collaboration' package in the ROS Packages folder with the one given in this repository.
* Open the 'human_baxter_collaboration' package, then navigate to config folder and open the params.yaml file. Under ROS_IP, insert the IP address of your machine.
* Compile packages with catkin_make
* Don't forget you need MoveIt framework for this project, thus install the binaries from [here](https://moveit.ros.org/install/).
* Clone the [baxter_common](https://github.com/RethinkRobotics/baxter_common) and [moveit_robots](https://github.com/ros-planning/moveit_robots) in the _src_ folder of your workspace. Once you're done, you should have four packages in your workspace: baxter_common, human_baxter_collaboration, moveit_robots, and ros_tcp_endpoint.
* Once all dependencies are resolved, start the roscore.
  ```
  roscore &
  ```
* Run the following command to initialize the ROS/Unity bridge and start communication with Unity (ensure the server communication is up and running, you should see the following line in the terminal 'Starting server on YOUR IP:10000').
  ```
  roslaunch human_baxter_collaboration human_baxter_collaboration.launch
  ```
* Open a new tab, run the following command to start trajectory planner server for robot's right arm.
  ```
  rosrun human_baxter_collaboration trajectory_planner_server_right.py
  ``` 
* Open a new tab, run the following command to start trajectory planner server for robot's left arm.  
  ```
  rosrun human_baxter_collaboration trajectory_planner_server_left.py
  ``` 
* Open a new tab, run the following command to start sofar_project node which works as Baxter robot controller.  
  ```
  rosrun human_baxter_collaboration sofar_project.py
  ```
* Once all the above setups are completed, proceed to the installation of Unity module. 
  
#### 2. On Windows
* In order to install the framework for human simulation, follow the steps [here](https://github.com/Daimler/mosim_core/wiki/InstallPrecompiled) to install the precompiled framework.
* Visit the [main repository](https://github.com/TheEngineRoom-UniGe/SofAR-Human-Robot-Collaboration) to download the Unity project folder, extract it, then open Unity Hub and ADD the project to your projects list using the associated button.
* Open the project.
* In the bar on top of the screen, open the Ros-TCP-Connection tab and replace the ROS_IP with the IP of the machine running ROS.
* If the previous steps have been successful, you should be able to enter Editor mode (via the Play button) and play the simulation.
* If the communication is running correctly, on UBUNTU you can echo the topics that are being exchanged between ROS and Unity.
Happy planning!

### Tips

1. If you experience a strange window when opening the Unity Project for the first time, simply do Quit, then reopen the project and it should not bother you further.
2. Should you experience issues in the communication between ROS and Unity, especially when publishing FROM ROS TO Unity, remember to disable the firewall of your PC, as it could interfere with the sending of messages over TCP.
3. When running your project, be sure to launch the ROS files BEFORE playing the Unity simulation, in order to have the server endpoint node up and running before initializing communication.

### Acknowledgements
Thanks to:
1. Simone Macciò, for helping out with the project and providing the [Unity environment and ROS files](https://github.com/TheEngineRoom-UniGe/SofAR-Human-Robot-Collaboration) for us to build further on.
2. Marco Gabriele Fedozzi, for helping out with the [docker image](https://hub.docker.com/r/hypothe/sofar_ros) loaded with all dependencies.
