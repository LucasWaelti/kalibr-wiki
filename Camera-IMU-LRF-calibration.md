Kalibr provides limited, experimental support for spatio-temporal laser range finder (LRF) calibration as detailed on in [1].



`kalibr_calibrate_imu_camera_laser --cam camchain-calibration_2015-10-09-10-48-02.yaml --imu imu_adis16448_ident.yaml --target april_6x6.yaml --imu-models calibrated --bag calibration_2015-11-05-13-39-04.bag --reprojection-sigma 0.1 --time-calibration --lrf-topic /scan --timeoffset-padding 0.1`


## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="general"></a>Rehder, Joern, Roland Siegwart, and Paul Furgale. "A General Approach to Spatiotemporal Calibration in Multisensor Systems." IEEE Transactions on Robotics 32.2 (2016): 383-398.