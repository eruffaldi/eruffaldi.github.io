
# macOS Homebrew #

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

Problem with embedded protobuf: OpenCVFindLibProtobuf.cmake

# macOS #

Download the OpenCV 3.3 source then

~~~~
mkdir buildosx
cd buildosx
CFLAGS=-march=native CXXFLAGS=-march=native cmake ..  -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_DOCS=OFF -DENABLE_CXX11=ON -DWITH_IPP=ON -DWITH_CUDA=ON 
~~~~

# mxe #

Download the OpenCV 3.3 source then

~~~~
mkdir buildmxe
cd buildmxe
$cmakemxe64 .. -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_DOCS=OFF -DENABLE_CXX11=ON -DWITH_IPP=OFF
~~~~

The above is the minimal situation: without CUDA, Python, IPP


## IPP ##

Issue: /usr/local/mxe/usr/bin/x86_64-w64-mingw32.shared.posix-ld: cannot find -lRunTmChk. This is due to the fact that the IPP has been built with Visual Studio and exposes some dependencies. The patch at http://code.opencv.org/issues/1906 provides some insights of the involved functions.

The library RunTmChck provides __security_cookie and _chkstk, and it can be found online (e.g. https://github.com/dblock/dotnetinstaller/blob/master/ThirdParty/Microsoft/Visual%20Studio%208/VC/lib/RunTmChk.lib). In the past it was provided with Windows SDK.

The next issues is the conversion of ippiw_win/lib/intel64/ipp_iw.lib and ippicv_win/lib/intel64/ippicvmt.lib 
