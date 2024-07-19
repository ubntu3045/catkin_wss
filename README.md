# ROS 2 Development Workspace Setup

# 1 Source ROS 2 environment
 
source /opt/ros/foxy/setup.bash
 
# 2 Create a new directory
 
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
 
# 3 Clone a sample repo

In the ros2_ws/src directory, run the following command:
git clone https://github.com/ros/ros_tutorials.git -b foxy-devel
 
# 4 Resolve dependencies
 
# cd if you're still in the ``src`` directory with the ``ros_tutorials`` clone
cd ..
rosdep install -i --from-path src --rosdistro foxy -y
  have all your dependencies, the console will return:
All required rosdeps installed successfully
# 5 Build the workspace with colcon
 
colcon build
The console  return the following message:
Starting >>> turtlesim
Finished <<< turtlesim [5.49s]


Once the build is finished, enter ls in the workspace root (~/ros2_ws) and you will see that  
build  install  log  src
 
6 Source the overlay
Before sourcing the overlay, it is very important that you open a new terminal, separate from the one where you built the workspace. Sourcing an overlay in the same terminal where you built, or likewise building where an overlay is sourced, may create complex issues.
In the new terminal, source your main ROS 2 environment as the “underlay”, so you can build the overlay “on top of” it:
source /opt/ros/foxy/setup.bash
Go into the root of your workspace:
cd ~/ros2_ws
In the root, source your overlay:
source install/local_setup.bash
Screenshot
![Screenshot from 2024-07-19 19-45-43](https://github.com/user-attachments/assets/fe1ccf6f-760c-4a10-a4c5-1f012c311e1e)
![Screenshot from 2024-07-19 16-27-36](https://github.com/user-attachments/assets/d681abd0-7993-4c77-845e-efbd60fe2233)

# Controlling-the-robot-arm-by-joint-state-publisher

## step1: 
```
mkdir catkin_wss
```

then you can go inside your new folder:
```
cd catkin_wss
```

then we are going to create a source (make sure it it exactly src inside thr catkin work space)
```
mkdir src
```

now make sure that you are inside the catkin_wss folder (not inside the src folder) then we can start to compile by running the command :
```
catkin_make
```

basicaally this is gonna compile everything in the workspace, install stuff, etc...

## step 2:
 now if we run the command ``` ls ``` we see that we have two new folders (build and devel)
 


if you go to the devel folder : ``` cd devel/ ``` then ```ls ```


![Screenshot from 2024-07-19 23-21-04](https://github.com/user-attachments/assets/025802d0-69c5-4a06-b555-cd6c9d57af72)

here we see something  called (setup.bash)
we will need to source this (setup.bash) script if we want to be able to use the code that we have written in our catkin workspace.

so, to source this we will need to:
```
source ~/catkin_wss/devel/setup.bash
```

once you have run this command you can use your custom ROS code

last thing here is to run ``` gedit ~/.bashrc``` then this window will appears


 at the end or the window we have the source line for our global ROS installation . so we will add this line ```source ~/catkin_wss/devel/setup.bash``` (after) the global ROS installation

![Screenshot from 2024-07-19 23-22-11](https://github.com/user-attachments/assets/d522b391-ea67-4e4c-b647-ce355279e13b)


 now save and quit the file. you should have those two lines so you can see your global ros installation as kind of a first level, and then your custom workspace here have the second level. you need to source both the global ROS installation and your catkin workspace, so you can use your code with ROS functionalities.

 ## Installing the package arduino_robot_arm
1-- Add the “arduino_robot_arm” package to “src” folder ```cd src``` then copy this command :
```
sudo apt install git
```



2- ```git clone https://github.com/smart-methods/arduino_robot_arm```


3- now go back to the (catkin_wss) using command ```cd ..``` ,then

```
rosdep install --from-paths src --ignore-src -r -y
```
![Screenshot from 2024-07-19 23-29-12](https://github.com/user-attachments/assets/fa61bf3a-0312-43b6-a803-c29f77bca48a)


4- run the command ```sudo apt-get install ros-noetic-moveit```

![Screenshot from 2024-07-19 23-30-00](https://github.com/user-attachments/assets/7b9d27c9-14e5-416e-9442-61238f6fa755)

5- run the command 
```
sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui
```

![Screenshot from 2024-07-19 23-31-00](https://github.com/user-attachments/assets/1acaa1c0-47e9-4f67-b085-45ebe1c34157)

6-
```
sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher
```
![Screenshot from 2024-07-19 23-31-36](https://github.com/user-attachments/assets/bc069e5a-3c10-4252-8d10-819f29608da7)


7-
```
sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control
```

![Screenshot from 2024-07-19 23-32-07](https://github.com/user-attachments/assets/210ff61f-0ba0-4d34-abf8-0137f984033e)

8-compile the package
```
catkin_make
```
![Screenshot from 2024-07-19 23-32-49](https://github.com/user-attachments/assets/3f758b6f-0b42-4eb4-a0a1-722d357efbd3)

## Controlling the motors

- when you run this command the widows will apears
  
```
roslaunch robot_arm_pkg check_motors.launch
```

 
![Screenshot from 2024-07-19 23-33-47](https://github.com/user-attachments/assets/5835aaae-d457-4870-b66e-70b67b718ed6)



## Gazebo
run the command :
```
roslaunch robot_arm_pkg check_motors_gazebo.launch
```
 

![Screenshot from 2024-07-19 16-33-23](https://github.com/user-attachments/assets/9ead9c3d-05a4-4a6b-83f1-61ceb5f33cb6)












 

