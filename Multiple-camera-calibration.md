#Multiple camera calibration with intrinsics
This tool estimates the intrinsic and extrinsic parameters of a multiple camera-system with non-shared overlapping fields of view. The image data is provided as a [ROS](https://www.ros.org) bag containing image streams for all cameras. The calibration routine will go through all images and select images using information theoretic measures in order to get a good estimate of the system parameters. (see [1](#jmaye))

Arbitrary combinations these camera and distortion models can be mixed in one calibration run. Have a look at [this page](supported-models) for a list of the supported camera and distortion models.

##How to use?
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

###1)Collect images
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

Create a ROS bag containing the raw image streams either by directly recording from a ROS sensor stream or by using the <font color='red'>bagcreater</font> script on a sequence of image files.

It is advised to lower the frequency of the camera streams to around 4 Hz while capturing the calibration data trying to avoid gathering too many images containing almost redundant information. Which would unnecessarily increase the number of images to be processing by the calibration.


###2)Running the calibration
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)
This sectioownload the sample dataset [here](http://awsome-link).
<font color='red'>bar</font>
1. Collect a ros bag containing the calibration image streams
2. Run the calibration
> rosrun aslam_camera_calibration calibrate --model pinhole-radtan pinhole-equi omni-radtan

###3) The output
The calibration will produce the following output files:

* **report-%BAGNAME%.pdf**: Report in PDF format. Contains all plots for documentation.
* **results-%BAGNAME%.txt**: Results in TXT format.
* **chain.yaml**: Results in YAML format. This file can be used as an input for the camera-imu calibrator

##An example run using a sample dataset
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="jmaye"></a> J. Maye, P. Furgale, R. Siegwart (2013). Self-supervised Calibration for Robotic Systems, In Proc. of the IEEE Intelligent Vehicles Symposium (IVS)

