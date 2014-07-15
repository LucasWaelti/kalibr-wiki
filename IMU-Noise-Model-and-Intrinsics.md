The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. This wiki page explains how to set these parameters and how to interpret them.

## The IMU Noise Model

The model used to describe IMU errors in Kalibr has two components:

1. Additive "white noise" that fluctuates rapidly
2. A slowly varying sensor "bias"

![equation](http://www.sciweavers.org/tex2img.php?eq=1%2Bsin%28mc%5E2%29%0D%0A&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance