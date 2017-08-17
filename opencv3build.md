
# macOS #

Tested with Sierra 10.12 using clang 8.1.0 and CUDA 8.0.61
~~~~
 brew update
 brew tap homebrew/science
 brew uninstall opencv3
 CFLAGS=-march=native CXXFLAGS=-march=native  brew install opencv3 --c++11 --with-contrib --with-cuda --with-ffmpeg --with-gstreamer --with-opengl --with-openni --with-qt --with-tbb --without-test
~~~~
In case of failure some upgrades are needed:
~~~~
 brew upgrade ceres-solver
 brew upgrade protobuf
~~~~
