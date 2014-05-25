#Supported calibration targets
Kalibr supports three different calibration target.

To simplify the data collection  Aprilgrid for the IMU-camera calibration. This is because the symmetrical natures of a checkerboard grid doesn't allow it easily to detect rotations above a certain threshold. For this reasons Aprilgrids have been introduced for the IMU-camera calibration which offer the following benefit:

* partially visible targets can be detected
* rotation is fully resolved (no flips)

The calibration targets are configured using a YAML configuration file which is passed to the calibration tools. Please find the configuration templates below.

##A) Aprilgrid
With the Aprilgrid partially visible targets can be detected without problems. This greatly simplifies the data collection and makes this grid the recommended target to use with this toolbox.

Aprilgrid PDFs can be downloaded here:

![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

or can be created according to your size requirements using the script here:

![example image](https://raw.githubusercontent.com/wiki/schneith/Kalibr-test/images/todo.gif)

The awsome [Apriltag implementation](http://people.csail.mit.edu/kaess/apriltags/) of M. Kaess is being used for tag extraction in this toolbox. (see [apriltags](#olson))

**aprilgrid.yaml**
```
target_type: 'aprilgrid' #gridtype
tagCols: 6               #number of apriltags
tagRows: 6               #number of apriltags
tagSize: 0.088           #size of apriltag, edge to edge [m]
tagSpacing: 0.3          #ratio of space between tags to tagSize
                         #example: tagSize=2m, spacing=0.5m --> tagSpacing=0.25[-]
```

##B) Checkerboard
The standard checkerboard pattern is supported using the following configuration:

**checkerboard.yaml**
```
target_type: 'checkerboard' #gridtype
targetCols: 6               #number of internal chessboard corners
targetRows: 7               #number of internal chessboard corners
rowSpacingMeters: 0.06      #size of one chessboard square [m]
colSpacingMeters: 0.06      #size of one chessboard square [m]
```

##C) Circlegrid
The standard OpenCV symmetric and asymmetric circle grid are supported using the following configuration:

**circlegrid.yaml**
```
target_type: 'circlegrid'  #gridtype
targetCols: 6              #number of circles (cols)
targetRows: 7              #number of circles (rows)
spacingMeters: 0.02        #distance between circles [m]
asymmetricGrid: False      #use asymmetric grid (opencv) [bool]
```

##Tips/Problems
* Make sure the printed target is as flat as possible. Best is to glue it to a rigid plate such as aluminum or acrylic glass.
* Most printers will scale the target during the printing process. Make sure to remeasure the important sizes and provide this data during the calibration.
* Reserve a white border around the calibration target (min. the size of one grid element)

## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="olson"></a>Edwin Olson (2011). AprilTag: A robust and flexible visual fiducial system. Proceedings of the IEEE International Conference on Robotics and Automation (ICRA), pp. 3400–3407

