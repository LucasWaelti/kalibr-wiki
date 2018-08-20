### Camera models
Kalibr supports the following projection models:

* **pinhole camera model (pinhole)** <br>
    (_intrinsics vector_: [fu fv pu pv])
* **omnidirectional camera model (omni)** <br>
    (_intrinsics vector_: [xi fu fv pu pv])
* **double sphere camera model (ds)** <br>
    (_intrinsics vector_: [xi alpha fu fv pu pv])
* **extended unified camera model (eucm)** <br>
    (_intrinsics vector_: [alpha beta fu fv pu pv])

The _intrinsics vector_ contains all parameters for the model:

* **fu, fv**: focal-length
* **pu, pv**: principal point
* **xi**: mirror parameter (only omni) 
* **xi, alpha**: double sphere model parameters (only ds) 
* **alpha, beta**: extended unified model parameters (only eucm) 

### Distortion models
Kalibr supports the following distortion models:

* **radial-tangential (radtan)** <br>
    (_distortion_coeffs_: [k1 k2 r1 r2])
* **equidistant (equi)**<br>
    (_distortion_coeffs_: [k1 k2 k3 k4])
* **fov (fov)**<br>
    (_distortion_coeffs_: [w])
* **none (none)**<br>
    (_distortion_coeffs_: [])

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="models"></a> J. Kannala and S. Brandt (2006). A Generic Camera Model and Calibration Method for Conventional, Wide-Angle, and Fish-Eye Lenses, IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 28, no. 8, pp. 1335-1340
