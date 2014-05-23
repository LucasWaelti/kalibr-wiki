#Installation

##A) CDE package
To remove necessity of building the code with all its pitfalls, we have packed the entire project with its dependencies into a [CDE](#guo) package. The only thing you will need to run this package is the 



##B) Building from source
1. Install the following requirements_
> sudo apt-get install BLOB

2. Limit the building threads to avoid memory problems during the build: <br\>
> export ROS_PARALLEL_JOBS="-j2

3. Build the code. Maybe grab a coffee, this will take a while...
> catkin_make


## References
Please cite the appropriate papers when using this library or parts of it in an academic publication.

1. <a name="guo"></a> Philip J. Guo. (2011). CDE: Run Any Linux Application On-Demand Without Installation.  USENIX Large Installation System Administration Conference (LISA). [homepage](http://www.pgbovine.net/cde.html)