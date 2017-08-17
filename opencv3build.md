
# macOS #

Tested with Sierra

 brew update
 brew tap homebrew/science
 brew uninstall opencv3
 CFLAGS=-march=native CXXFLAGS=-march=native  brew install opencv3 --c++11 --with-contrib --with-cuda --with-ffmpeg --with-gstreamer --with-opengl --with-openni --with-qt --with-tbb --without-test

In case of failure some upgrades are needed:

 brew upgrade ceres-solver
 brew upgrade protobuf
