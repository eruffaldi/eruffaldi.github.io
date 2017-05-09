
#Emanuele Ruffaldi Code Online
Here the listing of the public repositories, mainly on github. Legend on project size:
* XL for large project, most of them used regularly
* M for medium projects, some of them used
* U for little utilities
* EX for exercises and examples

## 3D,  Virtual Reality and Haptics
* [cocomr](https://github.com/cocomr) (XL) Compact Components framework and its Mixed Reality module (2014-,C++, with others)
* [chai3dproxy](https://github.com/eruffaldi/chai3dproxy) CHAI3D proxy code as standalone code
* [little3d](https://github.com/eruffaldi/little3d) Little 3D engine used in our robotic application (2015-2016,C++)
* [xvraam](https://github.com/eruffaldi/xvraamcpp) Tool for converting meshes in XVR AAM format to AssImp (2015,C++)
* [xvr_water](https://github.com/eruffaldi/xvr_water) XVR Water effect as developed for the SPRINT Rowing Trainer (2010,XVR)
* [openvr_exercies](https://github.com/eruffaldi/openvr_exercises) Cross-platform exercise using OpenVR (2016,C++)
  
## Computer Vision
* [coursevision](https://github.com/eruffaldi/coursevision2017) Practical part of the SSSA vision course 2017 using (Python, Jupyter)
* [livepython](https://github.com/eruffaldi/livepython) Live Python coding for OpenCV in the Browser (Python, OpenCV)
* [cvcamera_info](https://github.com/eruffaldi/cvcamera_info) Tool for manipulating the Camera Parameters under camera transformations e.g. crop, mirror, scaling (Python,OpenCV)
* [arucojson](https://github.com/eruffaldi/arucojson),  example Aruco program for obtaining JSON version of the visible from videos markers together with some additional details such as marker area (C/C++) - usable - (2015-2016)
* [calibration tool](https://github.com/eruffaldi/stereocalib) for RGB-D and stereo cameras in Python using OpenCV - active (2015-2016)
* [aruco pattern generator script](https://gist.github.com/eruffaldi/1e95c5fef80c0feda105) (Python) - PDF output, multiple pages control, physical size - usable
* [v4lsink device](https://github.com/eruffaldi/v4l2loopback_cpp) (EX) - create a simple V4L Linux sink as Virtual Camera
* [depthcapture](https://github.com/eruffaldi/depthcapture) image capture with compression for stereo (Zed) and depth cameras
* [pyoni](https://github.com/eruffaldi/pyoni) ONI manipulation tool in Python (registration, fix, cut..) and related [post](http://teslacore.blogspot.it/2015/09/swissknife-tool-for-oni-files.html) and initial [post](http://teslacore.blogspot.it/2013/11/recovering-truncated-openni-oni-files.html) (2013-2016)
* [gstreamerflow](https://github.com/eruffaldi/gstreamerflow) (EX) - gstreamer sink/source in C++
* [qtgst_appsink](https://github.com/eruffaldi/qtgst_appsink) (EX) - gstreamer sink in Qt without using QtGst
* [mp4 duration](https://github.com/eruffaldi/mp4-quicktime) (script) - extraction of frame duration from videos 

## Development Tools

* [CMakego](https://github.com/eruffaldi/cmakego), a simplified way to accessing libraries from C/C++ applications using CMake - active - related [blog post](http://teslacore.blogspot.it/2014/08/simpler-access-to-external-libraries-in.html) (2014-2016)
* [matlabaddons](https://github.com/eruffaldi/matlabaddons), a custom list of useful Matlab packages with an easy way to configure them - usable 
* [roboticvagrant](https://github.com/eruffaldi/roboticvagrant) and [linuxsetup](https://github.com/eruffaldi/linuxsetup), Linux setups for Robotics with vagrant and docker respectively - related [blog post](http://teslacore.blogspot.it/2015/01/packaging-your-robotic-vm-with-vagrant.html)
* [wine_vcpp](https://github.com/eruffaldi/wine_vcpp) (EX) Instructions for using command line Visual Studio inside Wine
* [editheader](https://gist.github.com/eruffaldi/51513cb4d656c797b129) (U) for editing headers of C/C++ managing license (Python)

## Math
This section deals meanly with manipulation of Tensors, Lie Algrebra tools and Multivariate Gaussians as used in my research activity
* [dliemat](https://github.com/eruffaldi/dliemat) Lie algebra and Distributions over Lie algrebra SE(3) in Matlab
* [matsemindex](https://github.com/eruffaldi/matsemindex) Semantic access to tensor indices in Matlab
* [nested tensors](https://github.com/eruffaldi/https://github.com/eruffaldi/nested-tensors) manipulation of nested tensors in Python and Matlab
* [multidimcxx](https://github.com/eruffaldi/multidimcxx) C++11 class for statically typed tensors and associated operations. Associated [blog post](http://teslacore.blogspot.it/2015/07/compile-time-c-multidimensional-arrays.html).
* [compare-mvn-tools](https://github.com/eruffaldi/compare-mvn-transform) Understanding Multivariate Normal Gaussian functions with Extended and Unscented filter
* [visualautodiff](https://github.com/eruffaldi/visualautodiff) Automatic backward differentiation in Simulink by connecting blocks, and associated [blog post](http://teslacore.blogspot.it/2016/09/visual-reverse-autodifferentiation-in.html)

## C++

* [pooledchannel](https://github.com/eruffaldi/pooledchannel) multithread channel class in C++ with several policies
* [yreflectcxx](https://github.com/eruffaldi/yreflectcxx) is a CLang based C++ reflection for extracting types and OpenMP information, related [post](http://teslacore.blogspot.it/2016/01/yet-another-clang-reflector-for-data.html)
* [cmm](https://github.com/eruffaldi/cmm) a C++ (ehm C--) compiler with code generation for x86 and DEC Alpha (1998)
* [cxxsumtime](https://github.com/eruffaldi/cxxsumtype)(EX) Algebreical Type for C++ with related [post](http://teslacore.blogspot.com/2014/06/c11-from-optional-to-sum-types.html)

## Data Tools

* [picopak](https://github.com/eruffaldi/picopak) experimental tool for keeping track of personal data packages using git as backend
* [anycat](https://gist.github.com/eruffaldi/a1026de3455caef8aad01c10f1ed1d8e) (U) bash script for generic decompression
* [boost_compress](https://github.com/eruffaldi/boost_compress) comparison of compression methods using Boost IO Streams and fork of [boost_lz4_filter](https://github.com/eruffaldi/boost_lz4_filter) for LZ4 streaming
* [nested_list_product](https://github.com/eruffaldi/nested_list_product) generalization of condition matrix generation for experiments and benchmarking
  
## ROS Tools
* [catkin_sub](https://github.com/eruffaldi/catkin_sub) (U) ROS tool for partial builds of large catkin projects
* [ros_picopro](https://github.com/eruffaldi/ros_picopro) ROS interface for Pico Projectors of libam7xxx family
* [matlab_ros_utils](https://github.com/eruffaldi/matlab_ros_utils) MATLAB ROS utilities to be used with MATALB rosbag [my fork](https://github.com/eruffaldi/matlab_rosbag)
* [ros_alt_realsense](https://github.com/eruffaldi/ros_alt_realsense) alternative ROS interface to Intel Realsense cameras based on Intel librealsense

## Matlab/Simulink specific

* [simulink rt time](https://github.com/eruffaldi/simsynctime) Simulink block for synchronizing simulation time with real-time, cross platform, used in several projects
* [matlab addons](https://github.com/eruffaldi/matlabaddons) Management of matlab toolboxes from Open Source projects with automatic configuration
* [matlab ranges](https://github.com/eruffaldi/matranges) Manipulation of ranges from datasets
* [binary tensor load](https://gist.github.com/eruffaldi/6719169197240722c039aedfb50f018b) (U) Loads a tensor from binary file

## Web Level

* [jsonbag](https://github.com/eruffaldi/jsonbag) JSON multipart response for modern browsers. Serverside in C++ Mongoose [blog post](http://teslacore.blogspot.it/2017/04/json-bag-binary-multipart-json-response.html)

## System Level
* [usbbandwidth](https://gist.github.com/eruffaldi/e84d2a0b1990c258cd22a3c20f5b80a6) (U)  Estimation of USB device bandwidth usage in Linux, related [post](http://teslacore.blogspot.com/2016/09/bandwidth-usage-for-usb-cameras-zed.html)
* [tinyptp](https://github.com/eruffaldi/tinyptp)(EX) Precision Time Protocol (PTP) minimal implementation aimed at embedded cases (2016)
* [UEFIBoot](https://github.com/eruffaldi/uefiboot) an example for writing UEFI applications in CMake/C++ - related [blog post](http://teslacore.blogspot.com/2016/02/starting-with-uefi-with-cmake-and.html) (2016)
* [PitOS](https://github.com/eruffaldi/pitos) (XL) an exercise of low-level OS writing and integration with Java without OS in the middle (2002)

## Course Material
* [Course on OpenMP and GPU](https://github.com/eruffaldi/course_openmpgpu) with associated [blog page](http://teslacore.blogspot.it/2016/04/short-lectures-on-openmp-and-cuda.html)
* [Course on Simulink](https://github.com/eruffaldi/course_simulink) 
* [Course on Vision](https://github.com/eruffaldi/coursevision2017) Practical part of the SSSA vision course 2017 using (Python, Jupyter)

## Research Tools
* [pytexeq](https://github.com/eruffaldi/pytexeq) command line LaTeX equation generation to images with cache
* [publicationlister](https://github.com/eruffaldi/publicationlister) (U) personal tool for publication listing based on BibTeX

## Other Contributions
* [amfext](pecl.php.net/package/amfext) initial developer of the amfext extension for PHP registered in PECL (2007). Amfext serializes messages in the Flash format.

## Coding Fun
* [lonewolf_graph](https://github.com/eruffaldi/lonewolf_graph) Tool for visualizing Lone Wolf hyperbooks and some graph analysis. Associated [blog post](http://teslacore.blogspot.it/2016/12/lone-wolf-story-graph.html)
* [directionpole](https://github.com/eruffaldi/directionpole) code for the Where is the Direction Pole [post](http://teslacore.blogspot.it/2014/12/where-is-my-direction-pole.html)

