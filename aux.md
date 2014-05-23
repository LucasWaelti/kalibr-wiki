#Camera/distortion models and calibration targets

## Camera and distortion models
The package implements the following camera models:

* pinhole
* omni

and the following distortion models:

* radial-tangential
* equidistant


##Supported calibration targets
Three different calibration target are supported which are configured using a YAML-file. Please find the configuration details on the following 

###Aprilgrid
The awsome [Apriltag implementation](http://people.csail.mit.edu/kaess/apriltags/) of M. Kaess is used for the tag extraction. (see [olson](#olson))


###Checkerboard

Sample checkerboard.yaml:

```
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

###Circlegrid


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="olson"></a>Edwin Olson (2011). AprilTag: A robust and flexible visual fiducial system. Proceedings of the IEEE International Conference on Robotics and Automation (ICRA), pp. 3400–3407
