## Camera models
The toolbox allows the calibration of the following projection models

* **pinhole** 
    (_intrinsics_: [fu fv pu pv])
* **omni** 
    (_intrinsics_: [xi fu fv pu pv])

**_intrinsics_** is the vector used in the camera-system yaml for the inrinsic parameter:

* fu, fv: focal-length (u,v) [px]
* pu, pv: principal point (u,v)  [px]
* xi: <font color='red'>name</font> [-]

## Distortion models
The following distortion models are available:

* **radial-tangential** 
    (_distortion_coeffs_: [k1 k2 r1 r2])
* **equidistant**
    (_distortion_coeffs_: [k1 k2 k3 k4])

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="jmaye"></a> J. Kannala and S. Brandt (2006). A Generic Camera Model and Calibration Method for Conventional, Wide-Angle, and Fish-Eye Lenses, IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 28, no. 8, pp. 1335-1340
