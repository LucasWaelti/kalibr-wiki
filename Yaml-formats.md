#YAML formats

##Camera system configuration (aka chain.yaml)


##Calibration target configuration


##IMU configuration
Each IMU in the calibration is configured using a YAML file. Please refer to the example below for details:

**




**imu0.yaml**
```
#Accelerometers
accelerometer_noise_density: 	0.006 	#Noise density (continous) <font color='red'>UNIT</font>
accelerometer_random_walk: 		0.0002   #Bias random walk <font color='red'>UNIT</font>

#Gyroscopes
gyroscope_noise_density: 		0.0004 	#Noise density (continous) <font color='red'>UNIT</font>
gyroscope_random_walk: 		4.0e-06  #Bias random walk <font color='red'>UNIT</font>

update_rate: 			200.0 	#Hz (used for discretization of the above values)
```





##Calibration target configuration
Please refer to the [Calibration targets](calibration-target) page.