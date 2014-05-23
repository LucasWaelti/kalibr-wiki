#Dynamic IMU to multi-camera system calibration
This tool calibrates the spatial and temporal parameters of an imu/camera pair.

Detailed information about the used approach is available in the following papers: [1](#paul1), [2](#paul2)


##Contents
* [Multiple camera calibration with intrinsics](#multiple-camera-calibration-with-intrinsics)
* [Dynamic IMU and multi-camera calibration](#dynamic-IMU-and-multi-camera calibration)
* [Tipps](#tipps)
* [Supported calibration targets](#supported-calibration-targets)
* [Sample datasets](#sample-datasets)


###Quick walkthrough
The following instructions briefly explain the calibration process. 

1. Collect calibration data either as 
  * a ROS bag (with image and imu topics)
  * a set of images and IMU data as a CSV file<br\>
   Please see the sample datasets for the data format.

2. Create an IMU, camera and target configration yaml-file.<br\>
  1. `IMU.yaml`: <br\>
     * IMU error statistics (default values should work with common MEMS IMUs)<br\>
     * rostopic for imu data<br\>
  2. `cam.yaml`: <br\>
     * camera intrinsic calibration<br\>
     * rostopic for image data<br\>
  3. `target.yaml`: <br\>
     * target type<br\>
     * target dimensions<br\>

  Templates can be found in the `yaml_example` folder of the `imu_camera_calibration` ROS package.

3. Run the calibration with

  * ROS bag:<br\>

        rosrun imu_camera_calibration calib_term.py --imu IMU.yaml --cam cam.yaml \
               --target target.yaml --bag mybag.bag

  * Images/CSV:<br\>

        rosrun imu_camera_calibration calib_term.py --imu IMU.yaml --cam cam.yaml \
               --target target.yaml --csv image.csv imu.csv

To observe the target corner extraction and get result plots you can add the `--show-all` flag.

More information is available using the help argument:<br\>
   ```rosrun imu_camera_calibration calib_term.py --h```

##Tips
* try to excite all six IMU axis evenly
* avoid shocks 
* keep the motion blur low
    * low shutter times
    * good illumination 
* avoid too flat angles between the camera axis and the calibration target
* hide external apriltags, if the aprilgrid is used 
* if you are using a calibration target with symmetries (checkerboard, circlegrid), try to avoid rotations over the symmetry, as this would lead to orientation flips in the 


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="paul1"></a>Paul Furgale, Joern Rehder, Roland Siegwart (2013). Unified Temporal and Spatial Calibration for Multi-Sensor Systems. In Proceedings of the IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), Tokyo, Japan.
1. <a name="paul2"></a>Paul Furgale, T D Barfoot, G Sibley (2012). Continuous-Time Batch Estimation Using Temporal Basis Functions. In Proceedings of the IEEE International Conference on Robotics and Automation (ICRA), pp. 2088–2095, St. Paul, MN.
