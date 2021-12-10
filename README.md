# multiple_socketcan_bridge
ROS socketCAN bridge node modified for multiple drivers
Originated from [ros_canopen](https://github.com/ros-industrial/ros_canopen).

## Installation
You can simply put this node along with ros_canopen nodes.
For example,
---
cd ~/catkin_ws/src
git clone https://github.com/ros-industrial/ros_canopen
cd ros_canopen
git clone https://github.com/yeongseok94/multiple_socketcan_bridge.git
---

## Usage
You can run this code using roslaunch.
---
roslaunch multiple_socketcan_bridge multiple_socketcan_bridge.launch
---
The `multiple_socketcan_bridge.launch` looks like:
---
<launch>
  <node ns="can0" pkg="multiple_socketcan_bridge" type="multiple_socketcan_bridge_node" name="multiple_socketcan_bridge_node" output="screen">
    <param name="can_device" value="can0" />
  </node>

  <node ns="can1" pkg="multiple_socketcan_bridge" type="multiple_socketcan_bridge_node" name="multiple_socketcan_bridge_node" output="screen" >
    <param name="can_device" value="can1" />
  </node>
  
  <node ns="can2" pkg="multiple_socketcan_bridge" type="multiple_socketcan_bridge_node" name="multiple_socketcan_bridge_node" output="screen" >
    <param name="can_device" value="can2" />
  </node>
  
  <node ns="can3" pkg="multiple_socketcan_bridge" type="multiple_socketcan_bridge_node" name="multiple_socketcan_bridge_node" output="screen" >
    <param name="can_device" value="can3" />
  </node>
</launch>
---
Here, every namespaces of the node and the corresponding private parameter `can_device` should match with your socketCAN device name. In this case above, the socketCAN device name were `can0`, `can1`, `can2`, `can3`.
You can simply check your socketCAN device name with:
---
ip link show
---
