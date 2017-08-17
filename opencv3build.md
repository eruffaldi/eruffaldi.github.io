
# macOS #

Tested with Sierra 10.12 using clang 8.1.0 and CUDA 8.0.61
~~~~
 brew update
 brew tap homebrew/science
 brew uninstall opencv3
 CFLAGS=-march=native CXXFLAGS=-march=native  brew install opencv3 --c++11 --with-contrib --with-cuda --with-ffmpeg --with-gstreamer --with-opengl --with-openni --with-qt --with-tbb --without-test
~~~~
By default CUDA is building over many architectures, https://en.wikipedia.org/wiki/CUDA specify CUDA_GENERATION=xxx, e.g. Kepler for GT 750M. This requires to edit the formula
~~~~
 brew edit opencv3 -c
~~~~
 

In case of failure some upgrades are needed:
~~~~
 brew upgrade ceres-solver
 brew upgrade protobuf
 brew upgrade protobuf-c
 brew link protobuf
~~~~


# mxe #

Download the OpenCV 3.3 source then

~~~~
mkdir buildmxe
cd buildmxe
$cmakemxe64 .. -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_DOCS=OFF
~~~~

The above is the minimal situation: without CUDA, Python, IPP
