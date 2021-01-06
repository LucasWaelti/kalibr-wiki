The _rolling shutter calibration_ tool provides full intrinsic calibration (projection, distortion and shutter parameters) of rolling shutter cameras [1].

## How to use?

### 1) Collect rosbag / images
Create a ROS bag containing the raw image data either by directly recording a rosbag from a ROS sensor stream or by using the _[bagcreater](bag-format)_ script on a sequence of image files.

The camera system is fixed and the calibration target is moved in front of the cameras to obtain the calibration images. 

### 2) Running the calibration

The calibration can be run using:
```
rosrun kalibr kalibr_calibrate_rs_cameras 
--bag [filename.bag] \
--model [MODEL_0 ... MODEL_N] \
--target [target.yaml] \
--topic  [TOPIC_0 ... TOPIC_N]  \
--inverse-feature-variance 1 \
--frame-rate [FRAMERATE]
```

Available rolling shutter camera models:
- `pinhole-radtan-rs`
- `pinhole-equi-rs`
- `omni-radtan-rs`

Sample command: 
```
rosrun kalibr kalibr_calibrate_rs_cameras --bag MYROSBAG.bag --model pinhole-radtan-rs --target aprilgrid.yaml \\
--topic /cam0/image_raw --feature-variance 1 --frame-rate 30
```

### 3) The output
The calibration will be printed to the screen.

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="othlu"></a>L. Oth, P. Furgale, L. Kneip, R. Siegwart (2013). Rolling Shutter Camera Calibration, In Proc. of the IEEE Computer Vision and Pattern Recognition (CVPR)

