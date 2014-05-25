## Camera models
The package allows the calibration of the following projection models

* **pinhole** (_intrinsics_: <font color='red'>[fu fv pu pv]</font>)
* **omni** (_intrinsics_: <font color='red'>[xi fu fv pu pv]</font>)

**_intrinsics_** is the vector used in the camera-system yaml for the inrinsic parameter:

* fu, fv: focal-length (u,v) [px]
* pu, pv: principal point (u,v)  [px]
* xi: <font color='red'>name</font> [-]

## Distortion models
The following distortion models are available:

* **radial-tangential** (distortion_coeffs: <font color='red'>k1 k2 r1 r2</font>)
* **equidistant** (distortion_coeffs: <font color='red'>[k1 k2 r1 r2]</font>)
