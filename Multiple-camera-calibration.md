#Multiple camera calibration with intrinsics
This tool allows you to calibrate the intrinsic and extrinsic parameters of a multiple camera system with non-shared overlapping fields of view. 

The following properties make it different from existing toolboxes:

* The image data is collected from a [ROS](https://www.ros.org) bag and the tool chooses which images to include in the optimization based on information theoretic measures (see [jmaye](#jmaye))
* Different camera and distortion models can be mixed in one optimization run.


##Quick start
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

###Collect images
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)


###Calibrate the system
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)
This sectioownload the sample dataset [here](http://awsome-link).

1. Collect a ros bag containing the calibration image streams
2. Run the calibration
> rosrun aslam_camera_calibration calibrate --model pinhole-radtan pinhole-equi omni-radtan

###Output
The calibration will produce the following output files:

* **report-%BAGNAME%.pdf**: Report in PDF format. Contains all plots for documentation.
* **results-%BAGNAME%.txt**: Results in TXT format.
* **chain.yaml**: Results in YAML format. This file can be used as an input for the camera-imu calibrator

###Example calibration using sample dataset
![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="jmaye"></a> J. Maye, P. Furgale, R. Siegwart (2013). Self-supervised Calibration for Robotic Systems, In Proc. of the IEEE Intelligent Vehicles Symposium (IVS)

