# iai_hsr_robocup

This package contains the representation of the robocup environment. The URDF of the environment is defined as an xacro in `./urdf/HSR_robocup.urdf.xacro`, which loads and uses the spatial data of a table and a shelf from `./yaml/semantic_map_manual_data.yaml`. Edit this yaml file to change the position and dimension of the corresponding furniture.

## launch

To launch only the URDF and the TF-frames of their joints, run:

```
roslaunch iai_hsr_robocup hsr_robocup_with_state_publisher.launch
```

There is another launch-file, which includes also the map server and snap-map-icp localisation from the `hsr_navigation` package. 
```
roslaunch iai_hsr_robocup hsr_maps.launch
```

Open up your Rviz and check the RobotModel with TF Prefix `environment` and Robot Description `kitchen_description`.

## region filter

To provide RoboSherlock with proper region to collect data from, you can generate a yaml-file that can be loaded into the region filter. Run the following command in any package you want, to generate the file at the current directory:

```
rosrun iai_hsr_robocup region_filter_setup.py
```

You can also specify your target file. The default is `semantic_map.yaml`. Change it like this:

```
rosrun iai_hsr_robocup region_filter_setup.py my_individual_happiness.yaml
```

while the path is still the directory you are calling from.

## semantic map

*knowrob required, get it at https://github.com/knowrob/knowrob, or https://github.com/daniel86/knowrob*

To generate an OWL representation from the xacro, first create an URDF from the xacro:

```
rosrun xacro xacro urdf/HSR_robocup.urdf.xacro > urdf/HSR_robocup.urdf
```

With `knowrob_srdl` you can then convert the URDF into an OWL file:

```
rosrun knowrob_srdl URDF2SRDL -u urdf/HSR_robocup.urdf -s owl/HSR_robocup.owl -i http://knowrob.org/kb/robocup.owl#
```

