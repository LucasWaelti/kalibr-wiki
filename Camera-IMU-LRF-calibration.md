Kalibr provides limited, experimental support for spatio-temporal laser range finder (LRF) calibration as detailed on in [1].

### Usage
This work marks an _extension_ to camera/IMU calibration. Accordingly, it extends the command line interface with a few LRF specific options, while all camera and IMU options remain valid.
These additional options are
* **--lrf-topic** The topic of the ROS scan message.
* **--q_bl** An initial guess for the rotation from the laser into the body frame as quaternion.
* **--t_bl** The corresponding, relative translation.

Note that the initial guess needs to be sufficiently accurate to yield an initial point cloud that allows for identification of planes. Please consider [2] for determining an initial guess in case coarse estimates fail to produce plane detections.

The following command spells out the options used to process the example dataset:
```
kalibr_calibrate_imu_camera_laser --cam ../camchain-calibration_2015-10-09-10-48-02.yaml --imu ../imu_adis16448_ident.yaml --target ../april_6x6.yaml --imu-models calibrated --bag ../calibration_2015-11-05-13-39-04.bag --reprojection-sigma 0.1 --time-calibration --timeoffset-padding 0.1 --lrf-topic /scan --q_bl -0.5 0.5 -0.5  0.5 --t_bl 0. 0. 0.
```

### <a name="dataset"></a>Dataset
The approach uses planes present in the environment

The corresponding dataset can be found [here](https://drive.google.com/file/d/0B4rISk5dxJScOEhXQ3loMUw1SGM/view?usp=sharing).

### General Comments


## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="general2016"></a>Rehder, Joern, Roland Siegwart, and Paul Furgale. "A General Approach to Spatiotemporal Calibration in Multisensor Systems." IEEE Transactions on Robotics 32.2 (2016): 383-398.
1. <a name="extrinsic2004"></a>Zhang, Qilong, and Robert Pless. "Extrinsic calibration of a camera and laser range finder (improves camera calibration)." Intelligent Robots and Systems, 2004.(IROS 2004). Proceedings. 2004 IEEE/RSJ International Conference on. Vol. 3. IEEE, 2004.