#YAML formats

##Camera system configuration (aka chain.yaml)

describe all the possible entries...
* camera_model
* time 
* to imu
* to last


chain evtl bild
imu0 -> cam0 -> cam1 -> cam2



**chain.yaml**
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
```

<font color='red'>INTRODUCE BETTER NAMINGS ...</font>



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