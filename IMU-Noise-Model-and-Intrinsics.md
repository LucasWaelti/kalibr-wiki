The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. Here, you can learn how to set these parameters and how to interpret them.

## The IMU Noise Model

The IMU measurement model used in Kalibr contains two types of sensor errors: <img src="https://latex.codecogs.com/svg.latex?{n}">, an additive noise term that fluctuates very rapidly ("white noise"), and <img src="https://latex.codecogs.com/svg.latex?{b}">, a slowly varying sensor bias. The angular rate measurement <img src="https://latex.codecogs.com/svg.latex?{%5Ctilde%5Comega}"> (in case of a gyro) is therefore written as:

<img src="https://latex.codecogs.com/svg.latex?{%5Ctilde%5Comega(t)=%5Comega(t)+b(t)+n(t)}">.

The same model (with different parameters, as we will later see) is used to model the accelerometer measurement errors. This model is tractable and often used.

**Additive "White Noise"** The rapid fluctuations in the sensor signal are modelled heuristically with an additive, independent white Gaussian noise process <img src="https://latex.codecogs.com/svg.latex?{n(t)}"> of strength <img src="https://latex.codecogs.com/svg.latex?{%5Csigma_g}"> in continuous-time as:

<img src="https://latex.codecogs.com/svg.latex?{n(t)=%5Cmathcal%7BN%7D(0,%5Csigma_g^2)}">

<img src="https://latex.codecogs.com/svg.latex?{E[n(t_1)n(t_2)]=%5Csigma_g^2%5Cdelta(t_1-t_2})">

In other words, the higher <img src="https://latex.codecogs.com/svg.latex?{%5Csigma_g}"> is, the more "noisy" your gyro measurements. The parameter `gyroscope_noise_density` in the [YAML file](yaml-formats) specifies exactly this noise strength <img src="https://latex.codecogs.com/svg.latex?{%5Csigma_g}">.

How you can determine this parameter for your particular gyro or accelerometer in practice will be explained below.

**Bias** In Kalibr, low variations in the sensor bias are modelled with a "Brownian motion" process, a "random walk".

## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance
