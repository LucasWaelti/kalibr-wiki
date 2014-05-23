#Kalibr

##Introduction
![](wiki_images/cam.jpg)

##Installation
###A) CDE package

###B) From source
1. Before you compile the repository code, you need to install the required
   dependencies:

        sudo apt-get install ros-groovy-desktop python-rosinstall ipython libeigen3-dev \
        libboost-all-dev doxygen libopencv-dev ros-groovy-vision-opencv \
        ros-groovy-image-transport-plugins python-software-properties \
        software-properties-common

2. Limit the building threads to avoid memory problems during the build: <br\>
    ```export ROS_PARALLEL_JOBS="-j2"```

3. Build the code.
    ```rosmake imu_camera_calibration```

##Authors
* Paul Furgale ([email](paul.furgale@mavt.ethz.ch))
* Jérôme Maye ([email](jerome.maye@mavt.ethz.ch))
* Jörn Rehder ([email](joern.rehder@mavt.ethz.ch))
* Thomas Schneider ([email](schneith@ethz.ch))

##License (BSD)
Copyright (c) 2014, Paul Furgale, Jérôme Maye and Jörn Rehder, Autonomous Systems Lab, ETH Zürich, Switzerland
Copyright (c) 2014, Thomas Schneider, Skybotix AG, Switzerland
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

1. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

1. All advertising materials mentioning features or use of this software must display the following acknowledgement: This product includes software developed by the <organization>.

1. Neither the name of the <organization> nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY <COPYRIGHT HOLDER> ''AS IS'' AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL <COPYRIGHT HOLDER> BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
