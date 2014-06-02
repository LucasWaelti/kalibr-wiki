The calibration validation tool extracts calibration targets from live ROS image streams and displays the image overlaid with the reprojections of the extracted corners. Further the reprojection error statistics are calculated and displayed for mono and as well as for inter-camera reprojections.

The tool must be provided with a calibration file for the camera system and for the calibration target. The output YAML file of the multi-camera calibrator can be used as the calibration input.

Usage:
> rosrun aslam_calibration validator --chain chain.yaml --target target.yaml
