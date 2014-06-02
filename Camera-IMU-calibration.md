The camera-imu calibration tool estimates the spatial and temporal parameters of an imu/camera pair. Image and IMU data is provided as a [ROS](https://www.ros.org) bag containing data streams for all cameras and the IMU. 

The calibration parameters are estimated in a full batch optimization using splines to model the pose of the camera-imu rig. Detailed information about the approach can be found in the following papers: (see [1](#paul1), [2](#paul2))

##How to use it

###1) Requirements
The intrinsic parameters of the IMU such as 

* scales
* axis misalignment
* nonlinearities

need to be estimated and its corrected beforehand. 

Further the following statistics need to be known:

* noise density
* bias random walk

This data has to be provided to the calibrator as an IMU-YAML file. Refer to this [page](yaml-formats) for the data format.


###2) Collect images
Create a ROS bag containing the raw image streams either by directly recording from a ROS sensor stream or by using the _[bagcreater](bag-format)_ script on a sequence of image files.

The calibration target is fixed in this calibration and the camera-imu system is moved in front of the target. Therefore it is important to have good illumination and to keep the cameras shutter times as low as possible to avoid motion blur while exciting the IMU.

Good results have been obtained by using a camera rate of 20 Hz while the IMU was recorded at 200 Hz. 

**Tips:**

* try to excite all six IMU axis evenly
* avoid shocks 
* keep the motion blur low
    * low shutter times
    * good illumination 
* if you are using a calibration target with symmetries (checkerboard, circlegrid), try to avoid rotations over the symmetry, as this would lead to orientation flips in the 

###3) Running the calibration
The tool must be provided with the following input:

* **--bag filename.bag**<br>
    ROS bag containing the image and IMU data<br>
* **--cam camchain.yaml**<br>
    intrinsic and extrinsic calibration parameters of the camera system. the output of the multiple-camera-calibration tool can be used directly here. (see [YAML formats](yaml-formats)<br>
* **--imu imu.yaml**<br>
    contains the IMU statistics and the IMU's topic (see [YAML formats](yaml-formats))<br>
* **--target target.yaml**<br>
    the calibration target configuration (see [Cailbration targets](#calibration-target))

The calibration can then be run using:
> kalibr_calibrate_imu_camera --bag [filename.bag] --cam [camchain.yaml] --imu [imu.yaml] --target [target.yaml]

The temporal calibration is turned off by default and can be enabled using the **--time-calibration** argument. More information about options is available using the help argument:<br\>
> kalibr_calibrate_imu_camera --h


###4) The output
The calibration will produce the following output files:

* **report-cam-%BAGNAME%.pdf**: Report in PDF format. Contains all plots for documentation.
* **results-cam-%BAGNAME%.txt**: Result summary as a text file.
* **camchain_cimu.yaml**: Results in YAML format. This file is based on the input ***camchain.yaml*** with added transformations (and time shifts) for all cameras with respect to the imu. Please check the used format [here](yaml-formats).

##An example run using a sample dataset
Download the sample dataset <font color='red'>here</font> and extract it. The archive will contain the bag-file, calibration target and imu configuration file.

> kalibr_calibrate_cameras --bag dataset_icc.bag --cam camchain.yaml --imu imu0.yaml --target aprilgrid_6x6.yaml


## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="paul1"></a>Paul Furgale, Joern Rehder, Roland Siegwart (2013). Unified Temporal and Spatial Calibration for Multi-Sensor Systems. In Proceedings of the IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), Tokyo, Japan.
1. <a name="paul2"></a>Paul Furgale, T D Barfoot, G Sibley (2012). Continuous-Time Batch Estimation Using Temporal Basis Functions. In Proceedings of the IEEE International Conference on Robotics and Automation (ICRA), pp. 2088–2095, St. Paul, MN.
