# region filter setup

This script uses the data from `semantic_map_manual_data.yaml` into `semantic_map.yaml`, an opencv yaml format, usable for the Robosherlock region filter. It is dependent on the package `iai_hsr_robocup`, which is located at <https://github.com/Suturo1819/iai_maps/tree/master/iai_hsr_robocup>, in our fork of iai_maps.

## usage

`region_filter_setup.py` uses tf data to parse the poses of regions into rotation matrices. First start

```
roslaunch iai_hsr_robocup hsr_robocup_with_state_publisher.launch
```

to get the TF tree running with the environment's poses. The run

```
rosrun suturo_perception_msgs region_filter_setup.py
```

to parse the TF frames into `semantic_map.yaml`, which will be either overwritten, or generated in the same directory as this script.

