Two sources for the toolbox are provided. Altough it is possible to use the CDE package to get the toolbox running we recommend to build the package from source using catkin (ROS build-system) as some of the tools will only work with a native ROS installation

* **building from source**<br>
    Depends on a working installation of ROS hydro with a catkin workspace. Binaries will run faster than with the CDE package and all tools can be used.

* **CDE package**<br>
    Using this package is the easiest way to get the toolbox working. All dependencies are packed within this package so no external dependencies need to be installed. Some tools will not work with this package (validator and focus tool)


##A) Using the CDE package
To remove necessity of building the code with all its pitfalls, we have packed the entire project with its dependencies into a [CDE](#guo) package. The only thing you will need to run this package is the 


##B) Building from source
1. Install the following requirements_
> sudo apt-get install BLOB
> pip iigraph....

2. Limit the building threads to avoid memory problems during the build: <br\>
> export ROS_PARALLEL_JOBS="-j2

3. Build the code. Maybe grab a coffee, this will take a while...
> catkin_make

sudo pip install python-igraph --upgrade

## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="guo"></a> Philip J. Guo. (2011). CDE: Run Any Linux Application On-Demand Without Installation.  USENIX Large Installation System Administration Conference (LISA). [homepage](http://www.pgbovine.net/cde.html)