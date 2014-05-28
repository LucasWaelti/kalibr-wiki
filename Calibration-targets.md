Kalibr supports three different calibration target. The Aprilgrid is the recommended grid to use in this toolbox due to the following benefits over the other targets:

* partially visible calibration boards can be used
* rotations of the target are fully resolved (no flips)

The calibration target is configured using a YAML configuration file which is passed to the calibration tool. Please find the configuration templates for the supported targets below.

###A) Aprilgrid
With the Aprilgrid partially visible targets can be detected without problems. This greatly simplifies the data collection and makes this grid the recommended target to use with this toolbox.

Aprilgrid PDFs can be downloaded here:

<font color='red'>http://Aprilgrid PDFs/</font>

or can be created according to your size requirements using the script here:

<font color='red'>createTargetPdf...</font>

**aprilgrid.yaml**
```
target_type: 'aprilgrid' #gridtype
tagCols: 6               #number of apriltags
tagRows: 6               #number of apriltags
tagSize: 0.088           #size of apriltag, edge to edge [m]
tagSpacing: 0.3          #ratio of space between tags to tagSize
                         #example: tagSize=2m, spacing=0.5m --> tagSpacing=0.25[-]
```

The awsome [Apriltag implementation](http://people.csail.mit.edu/kaess/apriltags/) of M. Kaess is used for tag extraction in this toolbox. [[1](#olson)]

###B) Checkerboard
The standard checkerboard pattern is supported using the following configuration:

**checkerboard.yaml**
```
target_type: 'checkerboard' #gridtype
targetCols: 6               #number of internal chessboard corners
targetRows: 7               #number of internal chessboard corners
rowSpacingMeters: 0.06      #size of one chessboard square [m]
colSpacingMeters: 0.06      #size of one chessboard square [m]
```

###C) Circlegrid
The standard OpenCV symmetric and asymmetric circle grid are supported using the following configuration:

**circlegrid.yaml**
```
target_type: 'circlegrid'  #gridtype
targetCols: 6              #number of circles (cols)
targetRows: 7              #number of circles (rows)
spacingMeters: 0.02        #distance between circles [m]
asymmetricGrid: False      #use asymmetric grid (opencv) [bool]
```

##Problems with the target extraction?
The *--show-extraction* argument can be used on both calibrators to show details of the calibration target extraction and might help to debug problems with calibration target extraction.

##Tips/Problems
* Make sure the printed target is as flat as possible. Best is to glue it to a rigid plate such as aluminum or acrylic glass.
* Most printers will scale the target during the printing process. Make sure to remeasure the important sizes and provide this data during the calibration.
* Reserve a white border around the calibration target of min. the size of one grid element (or the detection might be unsuccessful in certain lightning conditions)

## References
Please cite the appropriate papers when using this toolbox or parts of it in an academic publication.

1. <a name="olson"></a>Edwin Olson (2011). AprilTag: A robust and flexible visual fiducial system. Proceedings of the IEEE International Conference on Robotics and Automation (ICRA), pp. 3400–3407
