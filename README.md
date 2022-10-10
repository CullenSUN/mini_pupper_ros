# Mini Pupper ROS2

## 1. Installation
Ubuntu 20.04 + ROS2 Galatic is required.
```sh
cd ~
mkdir -p ros2_ws/src
cd ~/ros2_ws/src
git clone https://github.com/mangdangroboticsclub/mini_pupper_ros.git -b ros2
git clone https://github.com/mangdangroboticsclub/mini_pupper_description.git -b ros2
git clone --recursive https://github.com/chvmp/champ -b ros2
cd ..
rosdep install --from-paths src --ignore-src -r -y
colcon build
sudo apt-get install ros-galactic-teleop-twist-keyboard ros-galactic-cartographer-ros
```

## 2. Test in RVIZ
```sh
# Terminal 1
source ~/ros2_ws/install/setup.bash
ros2 launch mini_pupper_bringup bringup.launch.py

# Terminal 2
source ~/ros2_ws/install/setup.bash
rviz2 -d src/champ/champ_description/rviz/urdf_viewer.rviz

# Terminal 3
ros2 run teleop_twist_keyboard teleop_twist_keyboard
# Then control robot dog with your keyboard
```

## 3. Test in Gazebo
```sh
# Terminal 1
source ~/ros2_ws/install/setup.bash
ros2 launch mini_pupper_gazebo gazebo.launch.py

# Terminal 2
source ~/ros2_ws/install/setup.bash
rviz2 -d src/champ/champ_description/rviz/urdf_viewer.rviz

# Terminal 3
ros2 run teleop_twist_keyboard teleop_twist_keyboard
# Then control robot dog with your keyboard
```

## 4. Cartographer Test in Gazebo
```sh
# Terminal 1
source ~/ros2_ws/install/setup.bash
ros2 launch mini_pupper_gazebo gazebo.launch.py

# Terminal 2
source ~/ros2_ws/install/setup.bash
ros2 launch mini_pupper_navigation slam.launch.py use_sim_time:=true

# Terminal 3
ros2 run teleop_twist_keyboard teleop_twist_keyboard
# Then control robot dog with your keyboard
```
