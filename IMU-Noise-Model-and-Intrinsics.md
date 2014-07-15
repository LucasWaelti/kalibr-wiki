The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. This wiki page explains how to set these parameters and how to interpret them.

## The IMU Noise Model

The model used to describe IMU errors in Kalibr has two components:

1. Additive "white noise" that fluctuates rapidly
2. A slowly varying sensor "bias"

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default">
(E=mc^2)，$$x_{1,2} = \frac{-b \pm \sqrt{b^2-4ac}}{2b}.$$
</script>



## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance