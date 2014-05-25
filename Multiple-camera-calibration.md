This tool estimates the intrinsic and extrinsic parameters of a multiple camera-system with non-shared overlapping fields of view. The image data is provided as a [ROS](https://www.ros.org) bag containing image streams for all cameras. The calibration routine will go through all images and select images using information theoretic measures in order to get a good estimate of the system parameters. (see [1](#jmaye))

Arbitrary combinations these camera and distortion models can be mixed in one calibration run. Have a look at [this page](supported-models) for a list of the supported camera and distortion models.

##How to use?

###1) Collect images
Create a ROS bag containing the raw image streams either by directly recording from a ROS sensor stream or by using the <font color='red'>bagcreater</font> script on a sequence of image files.

It is recommended to lower the frequency of the camera streams to around 4 Hz while capturing the calibration data. This reduces the number of images to be processed by the calibrator containing almost redundant information and thus lower the runtime of the calibration.

###2) Running the calibration

The tool must at least be provided with the following arguments:

* **--bag filename.bag**<br>
    the rosbag containing the data
* **--topics TOPIC_0 ... TOPIC_N**<br>
    list of all camera topics in the bag  (matches the ordering of the --models)
* **--models MODEL_0 ... MODEL_N**<br>
    list of camera/distortion models to be calibrated. (matches the ordering of the --topics)
* **--target target.yaml**<br>
    the calibration target configuration (see [Cailbration targets](#calibration-target))

Note that the ordering of the topics and camera/distortion models match and determine the internal camera number in the calibration.

The calibration can then be run using:
> <font color='red'>rosrun blob blob</font>

It can happen that the optimization diverges right after processing the first few images due to a bad initial guess on the focal lengths. In this case just try to restart the calibration as the images for the initial guesses are select randomly.

###3) The output
The calibration will produce the following output files:

* **report-%BAGNAME%.pdf**: Report in PDF format. Contains all plots for documentation.
* **results-%BAGNAME%.txt**: Result summary as a text file.
* **chain.yaml**: Results in YAML format. This file can be used as an input for the camera-imu calibrator. Please see the <font color='red'>here</font> for the used format.

###4) Optional live validation (ROS only)
If your sensor provides live data on ROS topics the live validator can be used to verify the calibration on live streams. Please refer to <font color='red'>this page</font> on how to use this tool.

##An example run using a sample dataset
Download the sample dataset <font color='red'>here</font> and extract it. The archive will contain the bag-file and the calibration target configuration file.

**IMAGE OF CAMERA ARRANGEMENT**<br>
The dataset was recorded with the sensor system shown in the picture above. It contains four cameras which should be calibrated using the following models:

* cam0, cam1: pinhole projection / equidistant distortion
* cam2, cam3: omni projection / radial-tangential distortion

> <font color='red'>rosrun aslam_camera_calibration calibrate</font> --models pinhole-equi pinhole-equi omni-radtan omni-radtan --topics /cam0/image_raw /cam1/image_raw /cam2/image_raw /cam3/image_raw --bag dataset_mcc.bag --target aprilgrid_6x6.yaml

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="jmaye"></a> J. Maye, P. Furgale, R. Siegwart (2013). Self-supervised Calibration for Robotic Systems, In Proc. of the IEEE Intelligent Vehicles Symposium (IVS)

