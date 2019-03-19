# region filter setup

This script uses the data from `semantic_map_manual_data.yaml` into an opencv yaml format, usable for the Robosherlock region filter.

## usage

`region_filter_setup.py` uses TF data to parse the poses of regions into rotation matrices. First start

```bash
roslaunch iai_hsr_robocup hsr_robocup_with_state_publisher.launch
```

to get the TF tree running with the environment's poses. The script can be executed by running

```bash
rosrun iai_hsr_robocup region_filter_setup.py
```

to parse the TF frames into `semantic_map.yaml`, which will be generated in the current directory of your command line. You can specify a different path and filename as a parameter like this

```
rosrun iai_hsr_robocup region_filter_setup.py config/some_filename.yml
```

to insert the file in the `./config` subfolder of your current location, with the given filename `some_filename.yml`.