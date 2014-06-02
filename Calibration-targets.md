Kalibr supports three different calibration target. The Aprilgrid is the recommended grid to use due to the following benefits over the other targets:

* partially visible calibration boards can be used
* rotations of the target are fully resolved (no flips)

The calibration targets are configured using YAML configuration files which are passed to the calibration tools. Please find the configuration templates for the supported targets below.

###A) Aprilgrid
Partially visible Aprilgrids can be detected without problems. This greatly simplifies the data collection and makes this grid the recommended target to use.

Aprilgrid PDFs can be downloaded from the [Downloads](downloads) page or can be created according to your size requirements using the following script:
> kalibr_create_target_pdf --type apriltag --nx [NUM_COLS] --ny [NUM_ROWS] --tsize [TAG_WIDTH_M] --tspace [TAG_SPACING_PERCENT]

**aprilgrid.yaml**
```
target_type: 'aprilgrid' #gridtype
tagCols: 6               #number of apriltags
tagRows: 6               #number of apriltags
tagSize: 0.088           #size of apriltag, edge to edge [m]
tagSpacing: 0.3          #ratio of space between tags to tagSize
                         #example: tagSize=2m, spacing=0.5m --> tagSpacing=0.3[-]
```

**Make sure to hide all external Apriltags not belonging to the calibration target while collection the calibration dataset**

The awsome Apriltag implementation of M. Kaess is used for tag extraction in this toolbox. [[1](#olson),[2](#olson)]

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
1. <a name="kaess"></a>Michael Kaess. [http://people.csail.mit.edu/kaess/apriltags/](http://people.csail.mit.edu/kaess/apriltags/), Nov. 2013



