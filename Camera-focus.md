#Camera focus (not in CDE)

This [ROS](www.ros.org) node helps you with setting the focus of a camera in reproducible way. The tool subscribes to the camera's image topic and present you the live image along with a measure of focus. Point the camera at a scene with high frequency components (e.g. Siemens star) and adjust the focus while trying to minimize the calculated focus index.

The tool can be launched with:
> rosrun aslam_calibration camera_focus --topic /cam0/image_raw


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="focus"></a> Matej Kristan, Franjo Pernu. Entropy Based Measure of Camera Focus.  University of Ljubljana. Slovenia.






