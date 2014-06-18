The _multiple camera calibration_ tool estimates the intrinsic and extrinsic parameters of a multiple camera-system with the requirement that neighbouring cameras have overlapping fields of view. 

The image data is provided as a [ROS](https://www.ros.org) bag containing the image streams for all cameras. The calibration routine will go through all images and picks images based on information theoretic measures in order to get a good estimate of the system parameters. (see [1](#jmaye))

Arbitrary combinations of projection and distortion model can be combined in one calibration run. Have a look at [Supported models](supported-models) page for a list of available models.

##How to use?

###1) Collect images
Create a ROS bag containing the raw image streams either by directly recording from a ROS sensor stream or by using the _[bagcreater](bag-format)_ script on a sequence of image files.

The camera system is fixed and the calibration target is moved in front of the cameras to obtain the calibration images. 

It is recommended to lower the frequency of the camera streams to around 4 Hz while capturing the calibration data. This reduces the number of images containing almost redundant information and thus lower the runtime of the calibration.

###2) Running the calibration

The tool must be provided with the following input:

* **--bag filename.bag**<br>
    ROS bag containing the data
* **--topics TOPIC_0 ... TOPIC_N**<br>
    list of all camera topics in the bag. matches the ordering of --models
* **--models MODEL_0 ... MODEL_N**<br>
    list of camera/distortion models to be fitted. matches the ordering of --topics. (see [Supported models](supported-models))
* **--target target.yaml**<br>
    the calibration target configuration (see [Cailbration targets](#calibration-target))

Note that the ordering of the topics (--topics) and camera/distortion models (--models) arguments match order and determine the internal camera numbering in the output.

The calibration can be run using:
> kalibr_calibrate_cameras --bag [filename.bag] --topics [TOPIC_0 ... TOPIC_N] --models [MODEL_0 ... MODEL_N] --target [target.yaml]

It can happen that the optimization diverges right after processing the first few images due to a bad initial guess on the focal lengths. In this case just try to restart the calibration as the initial guesses are based on a random pick of images.

More information about options is available using the help argument:<br\>
> kalibr_calibrate_cameras --h

###3) The output
The calibration will produce the following output:

* **report-cam-%BAGNAME%.pdf**: Report in PDF format. Contains all plots for documentation.
* **results-cam-%BAGNAME%.txt**: Result summary as a text file.
* **camchain-%BAGNAME%.yaml**: Results in YAML format. This file can be used as an input for the camera-imu calibrator. Please check the format on the [YAML formats](yaml-formats) page.

###4) Optional live validation (ROS only)
If your sensor provides live data on ROS topics the validator tool can be used to verify the calibration. Please refer to the [Calibration validator](calibration-validator) page on how to use this tool.

##An example run using a sample dataset
Download the sample dataset from the [Downloads](downloads) page and extract it. The archive will contain the bag and the calibration target configuration file.

(https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/sensor_dataset.png)
The dataset was recorded with the sensor system shown in the picture above. It contains four cameras that should be calibrated using the following models:

* **cam0, cam1:** pinhole projection / equidistant distortion
* **cam2, cam3:** omni projection / radial-tangential distortion

> kalibr_calibrate_cameras --target april_6x6.yaml --bag static.bag --models pinhole-equi pinhole-equi omni-radtan omni-radtan --topics /cam0/image_raw /cam1/image_raw /cam2/image_raw /cam3/image_raw 

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="jmaye"></a> J. Maye, P. Furgale, R. Siegwart (2013). Self-supervised Calibration for Robotic Systems, In Proc. of the IEEE Intelligent Vehicles Symposium (IVS)

