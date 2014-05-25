All applications in this toolbox use ROS bags as a source for its sensor data (image and imu data)

##Using image files and IMU csv files
A bagcreater script is provided to use image files and/or IMU data for the calibration

###bagcreater
This script allows you to create a ROS bag from raw image files and optionally IMU data. The files have to be organized in folders as illustrated below for a system with two cameras and an IMU
>
dataset-dir<br>
├── cam0<br>
│   ├── 1385030208726607500.png<br>
│   ├──      ...<br>
│   └── 1385030212176607500.png<br>
├── cam1<br>
│   ├── 1385030208726607500.png<br>
│   ├──      ...<br>
│   └── 1385030212176607500.png<br>
└── imu0.csv<br>

The imu0.csv file is structured as follows (timestamps=[ns], omega=[rad/s], alpha=[m/s^2])
>
timestamp,omega_x,omega_y,omega_z,alpha_x,alpha_y,alpha_z<br>
1385030208736607488,0.5,-0.2,-0.1,8.1,-1.9,-3.3<br>
 ...<br>
1386030208736607488,0.5,-0.1,-0.1,8.1,-1.9,-3.3<br>

To create the ROS bag run the following command:
> rosrun aslam_calibration bagcreater --folder dataset-dir --output awsome.bag

The data will be written to the following topics:

* /cam0/image_raw
* /cam1/image_raw
* /imu0

###bagextractor
The bagextractor exports a ROS bag containing image and/or IMU data to image files and IMU data as csv  files.

Example usage:
> rosrun aslam_calibration bagextractor --image-topics /cam0/image_raw /cam1/image_raw --imu-topics /imu0 --output-folder dataset-dir --bag awsome.bag


