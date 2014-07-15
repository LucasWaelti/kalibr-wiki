The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. Here, you can learn how to set these parameters and how to interpret them.

## The IMU Noise Model

The IMU measurement model used in Kalibr contains two types of sensor errors: <img src="https://latex.codecogs.com/svg.latex?{n}">, an additive noise term that fluctuates very rapidly ("white noise"), and <img src="https://latex.codecogs.com/svg.latex?{b}">, a slowly varying sensor bias. The angular rate measurement <img src="https://latex.codecogs.com/svg.latex?{%5Ctilde%5Comega}"> (in case of a gyro) is therefore written as:

<img src="https://latex.codecogs.com/svg.latex?{%5Ctilde%5Comega(t)=%5Comega(t)+b(t)+n(t)}">.

**Additive "White Noise"**


## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance
