##Camera-system calibration file (aka chain.yaml)

This YAML file includes the complete parameter set for the calibration of the camera intrinsic and extrinsic parameters as well as the spatial and temporal calibration parameters of the IMU with respect to the cameras.

Each camera has the following parameters:

* **camera_model**<br>
    camera projection type (pinhole / omni)
* **intrinsics**<br>
    vector containing the intrinsic parameters for the given projection type. elements are as follows:<br>
    pinhole: [fu fv pu pv] <br>
    omni: [xi fu fv pu pv] <br>
    see [Supported models](supported-models) for more information<br>
* **distortion_model**<br>
    lens distortion type (radtan / equidistant)<br>
* **distortion_coeffs**<br>
    parameter vector for the distortion model<br>
    see [Supported models](supported-models) for more information<br>
* **T_cn_cnm1**<br>
    extrinsic parameters, always with respect to the last camera in the chain<br>
    (e.g. cam1: T_cn_cnm1 = T_c1_c0)<br>
* **T_cam_imu**<br>
    IMU extrinsics: tranformation from IMU-frame to camera frame<br>
* **time**<br>
    IMU extrinsics: tranformation from IMU-frame to camera frame<br>

* **rostopic**<br>
    topic of the camera's image stream
* **resolution**<br>
    camera resolution [width,height]


**Example chain.yaml**
```
cam0:
  camera_model: omni
  distortion_coeffs: [-0.3524047797899213, 0.16207450943423096, 0.00036919741711283124,
    0.000988523976270618]
  distortion_model: radtan
  intrinsics: [0.671111239995445, 770.7765589675081, 770.5559465743702, 362.1635863019238,
    247.88842203540298]
  resolution: [752, 480]
  rostopic: /cam0/image_raw
  trafo_cam_imu:
  - [0.014061452055637302, 0.9997399667393116, -0.0179520046281176, 0.07051165610399869]
  - [-0.9998860726109333, 0.01415751265554327, 0.005235134582067706, -0.01482053746550415]
  - [0.0054879290056671325, 0.017876345809171246, 0.9998251441605879, -0.0008669839765732394]
  - [0.0, 0.0, 0.0, 1.0]
cam1:
  baseline_last_to_this_cam:
  - [0.9999963219239997, 0.002667912895867444, 0.00048824097823761936, -0.10998811687147413]
  - [-0.0026721458237613386, 0.9999569589497798, 0.008884812018572488, 0.0003133265658200174]
  - [-0.0004645160592714478, -0.008886083990649619, 0.9999604100843904, -0.00041422980563141245]
  - [0.0, 0.0, 0.0, 1.0]
  camera_model: omni
  distortion_coeffs: [-0.34330808866302887, 0.14844603008818044, -0.0003074632859414297,
    0.0013186394350600886]
  distortion_model: radtan
  intrinsics: [0.7476616047651173, 805.0992800974523, 805.1201800399643, 376.61967341034676,
    256.0786828765575]
  resolution: [752, 480]
  rostopic: /cam1/image_raw
  trafo_cam_imu:
  - [0.011396470820857374, 0.9997827885948853, -0.01744981610976558, -0.03951668331483825]
  - [-0.999831851497067, 0.011644280296453924, 0.014166138087881374, -0.014702693425226551]
  - [0.01436625159102594, 0.017285437969947488, 0.9997473803163531, -0.001182236714303278]
  - [0.0, 0.0, 0.0, 1.0]

```

##IMU configuration
Each IMU in the calibration is configured using a YAML file. Please refer to the example below for details:

**imu0.yaml**
```
#Accelerometers
accelerometer_noise_density: 	0.006 	#Noise density (continous) [UNIT]
accelerometer_random_walk: 		0.0002   #Bias random walk [UNIT]

#Gyroscopes
gyroscope_noise_density: 		0.0004 	#Noise density (continous) [UNIT]
gyroscope_random_walk: 		4.0e-06  #Bias random walk [UNIT]

update_rate: 			200.0 	#Hz (used for discretization of the above values)
```

<font color='red'>INSERT UNITS ABOVE!</font>


##Calibration target configuration
Please refer to the [Calibration targets](calibration-target) page.