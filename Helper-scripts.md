#Helper scripts


##Camera focus
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

##ROS bag dataset creater/extractor
###bagcreater
This script allows you to create a ROS bag from raw image files and optionally IMU data. The files have to be organized in folders as illustrated below for a system with two cameras and an IMU.

>
dataset-dir
├── cam0
│   ├── 1385030208726607500.png
│   ├──      ...
│   └── 1385030212176607500.png
├── cam1
│   ├── 1385030208726607500.png
│   ├──      ...
│   └── 1385030212176607500.png
└── imu0.csv


The imuN.csv file is structured as follows:
>
timestamp,omega_x,omega_y,omega_z,alpha_x,alpha_y,alpha_z
1385030208736607488,0.5,-0.2,-0.1,8.1,-1.9,-3.3
...
1386030208736607488,0.5,-0.1,-0.1,8.1,-1.9,-3.3

To create the ROS bag run the following command:
> rosrun aslam_calibration bagcreater --folder dataset-dir --output awsome.bag

The data will be written to the following topics:

* /cam0/image_raw
* /cam1/image_raw
* /imu0



![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

##Calibration validation
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

