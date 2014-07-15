The [Camera-IMU calibration](Camera-IMU-calibration) routine needs to know how "noisy" your IMU is. This is specified in your [IMU configuration YAML file](yaml-formats) before you start the calibration. This wiki page explains how to set these parameters and how to interpret them.

## The IMU Noise Model

The model used to describe IMU errors in Kalibr has two components:

1. Additive "white noise" that fluctuates rapidly
2. A slowly varying sensor "bias"



## How to Obtain the Parameters

### From the Datasheet of the IMU
### From the Allan Variance

<p>
  Here is some inline latex rendered by 
  Mathjax: Let \( \epsilon > 0 \).
</p>

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>