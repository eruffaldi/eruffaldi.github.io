
# Camera-Robot Calibration Manual for RAMCIP

There are two main camera-robot calibration elements in the RAMCIP robot

1) Projector Intrinsics and Camera-Projector 
2) Camera-Body 

Calibration is provided via the external package: https://bitbucket.org/eruffaldi/ramcip_calib_sssa and it follows a common approach across the different types of calibration. The steps are the following:

1) Capture with tagging of relevant frames
2) Extraction of YAML files expressing the calibration problem
3) Computation and output of the results in usable form

These are the data flowing in the three steps

1) Capture produces a bag file
2) Extraction takes the bag file and produces YAML files in a folder
3) Computation takes YAML files and produces output as YAML file for calibration or a line for URDF

# Alternate ROS Core

When step 2 is executed offline on a real robot it is necessary to create an Alternate ROS Core environment so that there is no interference with the main robot pub-sub system.

On Terminal A
```
export ROS_MASTER_URI=http://127.0.0.1:16666 
roscore -p 16666
rosparam set use_sim_time true
export PS1="\u@\H:\w ALTCORE$ "
```

On Terminal B we launch the following before any Phase 2 command
```
export ROS_MASTER_URI=http://127.0.0.1:16666 
export PS1="\u@\H:\w ALTCORE$ "
```

TODO: make two script altroscorestart.sh, altroscore.sh

# Camera-Projector

## Physical Setup

Robot in front of a white wall so that the motion of the head in the range specified is projected over the wall as a single flat surface. Eventually modify the focus lever.

## Software Setup

Assuming the robot controlle ready

We start the camera
```
roslaunch ramcip_human_tracking ramcip_human_tracker.launch
```

On PC2 we start the head service
```
roslaunch ramcip_head_action look_around.launch
```

## Capture Start

Shell 1: On PC1 we start projection and recording
```
export DISPLAY=:0
xset s activate
roslaunch ramcip_calib_sssa calib_k1ar_capture.launch
```

Shell 2: On PC2 we start the motion of the head. The range of the head can be controlled modifying the file ramcip_head_action/launch/look_around.launch modifying the pan/tilt == yaw/pitch joint angles in radians.

```
rosrun ramcip_head_action look_around_client.py
```

The file look_around.launch specifies the number of interval. When the robot stops moving it is possible to stop Shell 1 and verify if the resulting file is correct:

```
rosbag info captureK1AR.bag | grep boardk1 
rosbag info captureK1AR.bag | grep trigger
```

## Extraction

Inside the ALT ROS environment:
```
roslaunch ramcip_calib_sssa calib_k1ar_calib.launch inputbag:=${PWD}/captureK1AR.bag with_inputbag:=true action:=save inputbag_rate:=2
find calibk1ar | grep yaml | wc -l
```

Then calibration:
```
roslaunch ramcip_calib_sssa calib_k1ar_calib.launch action:=calibload
```
