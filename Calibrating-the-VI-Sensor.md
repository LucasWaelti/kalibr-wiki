![VI-Sensor](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/visensor.jpg)

This page will guide you through the calibration of the VI-Sensor (visual-inertial sensor). The intrinsics and extrinsics of the camera system as well as the transformation between the cameras and the IMU will be calibrated.

More information about the VI-Sensor can be found [here](http://www.skybotix.com/).


##Procedure

1. prepare the sensor
1. setting the focus
1. collect calibration data
    1. in-/extrinsics calibration (static calibration)
    1. imu-camera calibration (dynamic calibration)
1. run the calibration
    1. in-/extrinsic camera calibration
    1. camera-IMU calibration
1. collect results


##Requirements

* ROS sensor driver is running (image/imu data)
* good Aprilgrid target (<font color='red'>yaml</font> /  <font color='red'>pdf</font>)
* Siemens star (or similar camera focus test pattern)
* IMU configuration for ADIS16448 (<font color='red'>yaml</font>)


##1) Sensor preparation

1. make sure the sensor publishes all image and imu streams to ROS
1. minimize the motion blur with a good light source and by reducing the shutter times:
    Shutter times can be set using the following commands:

    >rosrun dynamic_reconfigure dynparam set /slam_sensor "{'cam0_agc_enable': 0, 'cam0_aec_enable': 0, 'cam0_coarse_shutter_width': 300}"<br>
    >rosrun dynamic_reconfigure dynparam set /slam_sensor "{'cam1_agc_enable': 0, 'cam1_aec_enable': 0, 'cam1_coarse_shutter_width': 300}"

    Observe the result on an image window and tweak the shutter until you get a good image:

    > rosrun image_view image_view image:=/cam0/image_raw &<br>
rosrun image_view image_view image:=/cam1/image_raw &


##2) Setting the focus

1. point the cameras on a Siemens star (or similar pattern)
1. start the focus tool

    >rosrun aslam_camera_calibration --topic /cam0/image_raw /cam1/image_raw

1. set the focus of both cameras by:
    1. reducing the interference visible around the center of the Siemens star
    1. minimizing the focus measure provided by the tool

Make sure a Teflon band or thread-locking glue prevents unintentional focus changes after this step.


##2) Collect calibration data
In this step we need to collect two calibration datasets with the following properties:

1. **static dataset (in-/extrinsic calibration of the cameras)**
    * attach the sensor somewhere and move the target
    * limit the camera streams to ~4 Hz
    * make sure to cover the entire field of view of the camera
    * use skewed views and varying distances to the calibration target

    view images with:
    >rosrun image_view image_view image:=/cam0/image_raw &<br>
rosrun image_view image_view image:=/cam1/image_raw &

    record bag with:
    >rosbag record /cam0/image_raw  /cam1/image_raw -O static.bag


1. **dynamic dataset (spatial camera-imu calibration)**
    * move the sensor (target is fixed)
    * cameras should run at 20 Hz and IMU at 200 Hz
    * try to excite all rotation and acceleration axis of the IMU
    * avoid shocks
    * good illumination and shutter times are crucial here (to avoid motion blur while exciting the IMU)
    >rostopic hz /cam0/image_raw<br>
    rostopic hz /cam1/image_raw<br>
    rostopic hz /imu0

    view images with:
    >rosrun image_view image_view image:=/cam0/image_raw &<br>
rosrun image_view image_view image:=/cam1/image_raw &

    record bag with:
    >rosbag record /cam0/image_raw  /cam1/image_raw /imu0 -O dynamic.bag


##3) Run the calibration
1. calibration of camera in/extrinsics
    1. run calibration
    > rosrun aslam_camera_calibration --models pinhole-equi pinhole-equi --topics /cam0/image_raw /cam1/image_raw --bag static.bag --target aprilgrid_6x6.yaml
    1. inspect the result plots
    1. verify calibration on the live image stream
    > rosrun aslam_calibration --chain chain.yaml --target aprilgrid_6x6.yaml

1. camera-imu calibration
    1. run calibration
    > rosrun imu_camera_calibration calibrate --cam chain.yaml --target aprilgrid_6x6.yaml --imu imu0.yaml --bag dynamic.bag
    1. inspect the result plots
        * make sure the predicted accelerations & angular velocities fit the IMU measurements
        * reprojection errors should be in a normal range

##4) Collect results
Both calibrators have written reports to the working directory containing the plots shown during the calibration. Further a _chain.yaml_ has been written by the camera calibrator and is extended by the imu-camera calibrator with its results to the file _chain_cimu.yaml_. Please refer to <font color='red'>this page</font> for more detail about the formats.