Two sources for the toolbox are provided. Altough it is possible to use the CDE package to get the toolbox running we recommend to build the package from source using catkin (ROS build-system) as some of the tools will only work with a native ROS installation

* **building from source**<br>
    Depends on a working installation of ROS hydro with a catkin workspace. Binaries will run faster than with the CDE package and all tools can be used.

* **CDE package**<br>
    Using this package is the easiest way to get the toolbox working. All dependencies are packed within this package so no external dependencies need to be installed. Some tools will not work with this package (validator and focus tool)


##A) Using the CDE package
To remove necessity of building the code with all its pitfalls, we have packed the entire project with its dependencies into a [CDE](#guo) package. The only thing you will need to run this package is the 


##B) Building from source
The source build has been tested on Ubuntu 12.10 with ROS hydro.

1. Install ROS hydro
    see [ros.org](http://wiki.ros.org/ROS/Installation) for more information

1. Install the following dependencies:
    >sudo apt-get install python-setuptools python-rosinstall ipython libeigen3-dev libboost-all-dev doxygen libopencv-dev ros-hydro-vision-opencv ros-hydro-image-transport-plugins ros-hydro-cmake-modules python-software-properties software-properties-common libpoco-dev python-matplotlib python-git python-pip ipython libtbb-dev libblas-dev liblapack-dev

    sudo pip install python-igraph --upgrade

1. Create a catkin workspace
    mkdir -p ~/kalibr_workspace/src
    cd ~/kalibr_workspace/src
    source /opt/ros/hydro/setup.bash
    catkin_init_workspace

1. Clone the source repo into the catkin workspace src folder
    cd ~/kalibr_workspace/src
    git clone https://github.com/ethz-asl/kalibr.git

1. Build the code. Maybe grab a coffee, this will take a while...
    depending on the amount of RAM you have, you might need to reduce the build threads, due to heavy templating (e.g. add -j4 to catkin_make)

    > cd ~/kalibr_workspace
    catkin_make -j2


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="guo"></a> Philip J. Guo. (2011). CDE: Run Any Linux Application On-Demand Without Installation.  USENIX Large Installation System Administration Conference (LISA). [homepage](http://www.pgbovine.net/cde.html)