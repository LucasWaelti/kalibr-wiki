The following two sources for the toolbox are available:

* **building from source**<br>
    Depends on a working installation of ROS indigo and a catkin workspace. Binaries will run faster than with the CDE package and all tools are available.

* **CDE package**<br>
    This package is the easiest and fastest way to get the toolbox running. All dependencies are packed within this package and no external dependencies are required. The [Camera focus](camera-focus) and [Calibration validator](calibration-validator) tools aren't available with the CDE-package as they require a native ROS installation.

**NOTE:** It is recommended to build the toolbox from source using a native ROS installation to make all tools available.

## A) Using the CDE package (only 64bit systems)
To remove the necessity of installing ROS and building the toolbox from source, a [CDE](#guo) package is provided that packs the toolbox and all its dependencies in a chroot-like environment. To install this package follow these steps:

1. Download the most recent package from the [Downloads](downloads) page.

1. Extract the archive using:

    > tar xfvz kalibr.tar.gz

1. Either you can run the tools directly from the cde-package folder
    **or/and**
    add the package folder to the system path using:

    > export PATH="**/cde/package/path**:$PATH"

    to use the tools more conveniently.

## B) Building from source
To build the toolbox from source follow these steps (tested on Ubuntu 14.04 with ROS indigo):

1. Install ROS indigo <br>
    see [ros.org](http://wiki.ros.org/ROS/Installation) for more information

    Example installation on Ubuntu 14.04 and ROS indigo:

    >sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu trusty main" > /etc/apt/sources.list.d/ros-latest.list'
<br>
    wget http://packages.ros.org/ros.key -O - | sudo apt-key add - <br>
    sudo apt-get update  <br>
    sudo apt-get install ros-indigo-desktop python-rosinstall python-rosdep -y <br>
    rosdep init <br>
    rosdep update <br>

1. Install the build and run dependencies:

    >sudo apt-get install python-setuptools python-rosinstall ipython libeigen3-dev libboost-all-dev doxygen libopencv-dev ros-indigo-vision-opencv ros-indigo-image-transport-plugins ros-indigo-cmake-modules python-software-properties software-properties-common libpoco-dev python-matplotlib python-scipy python-git python-pip ipython libtbb-dev libblas-dev liblapack-dev python-catkin-tools libv4l-dev <br> <br>
    sudo pip install python-igraph --upgrade

1. Create a catkin workspace<br>

    >mkdir -p ~/kalibr_workspace/src <br>
    cd ~/kalibr_workspace <br>
    source /opt/ros/indigo/setup.bash <br>
    catkin init <br>
    catkin config --extend /opt/ros/indigo <br>
    catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release

1. Clone the source repo into your catkin workspace _src_ folder <br>
    >cd ~/kalibr_workspace/src <br>
    git clone https://github.com/ethz-asl/Kalibr.git

1. Build the code using the _Release_ configuration.
    depending on the available memory, you might need to reduce the build threads (e.g. add -j2 to catkin_make) <br>

    > cd ~/kalibr_workspace <br>
    catkin build -DCMAKE_BUILD_TYPE=Release -j4

    Grab a coffee, this will take a while... <br>

1. Once the build is finished you have to source the catkin workspace setup to use Kalibr

    > source ~/kalibr_workspace/devel/setup.bash

More information on building with catkin and ROS can be found [here](http://wiki.ros.org/catkin/Tutorials).

## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="guo"></a> Philip J. Guo. (2011). CDE: Run Any Linux Application On-Demand Without Installation.  USENIX Large Installation System Administration Conference (LISA). [homepage](http://www.pgbovine.net/cde.html)