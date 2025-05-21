# unitreego2_ros2
the unitree go2 controll repository

## How to use 
Before colcon build, you should update packages.
And, install dependecies. 
at colcon_ws, you should perform below 
```bash
sudo apt update && upgrade
sudo apt install ros-humble-rmw-cyclonedds-cpp
sudo apt install ros-humble-rosidl-generator-dds-idl
```

build
```bash
git clone https://github.com/eclipse-cyclonedds/cyclonedds -b releases/0.10.x 
colcon build --symlink-install  --packages-select cyclonedds
source install/setup.bash

colcon build --symlink-install 
```

change networkinterface to one connected go2 so check it your local terminal
```bash
ip addr
```

```bash
#!/bin/bash
echo "Setup unitree ros2 environment"
source /opt/ros/humble/setup.bash
source /home/colcon_ws/install/setup.bash
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
export CYCLONEDDS_URI='<CycloneDDS><Domain><General><Interfaces>
                            <NetworkInterface name="enx68da73a4b276" priority="default" multicast="default" />
                        </Interfaces></General></Domain></CycloneDDS>'
```
