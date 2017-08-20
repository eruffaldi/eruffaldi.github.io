
# macOS Homebrew #
STATUS: embedded protbuf error

Running with Sierra 10.12 using clang 8.1.0 and CUDA 8.0.61
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

# macOS Source #

Download the OpenCV 3.3 source then

~~~~
mkdir buildosx
cd buildosx
CFLAGS=-march=native CXXFLAGS=-march=native cmake ..  -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_DOCS=OFF -DENABLE_CXX11=ON -DWITH_IPP=ON -DWITH_CUDA=ON -DWITH_OPENGL=ON 
~~~~

For reducing CUDA compilation times specify CUDA_GENERATION as above.

Qt: this requires -DWITH_QT=ON and to make Qt5 accessible to the installer. The problem is that qt5 from brew is not automatically linked because of incompatibility. We need to make it visible.

~~~~
PATH=$PATH:/usr/local/opt/qt/bin
~~~~

# mxe #


Download the OpenCV 3.3 source then

~~~~
mkdir buildmxe
cd buildmxe
CXXFLAGS=-DSTRSAFE_NO_DEPRECATE $cmakemxe64 .. -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_DOCS=OFF -DENABLE_CXX11=ON -DWITH_IPP=ON -DWITH_LAPACK=OFF
~~~~

## Patches ##
Edit modules/videoio/cap_dshow.cpp adding the following to disable a sprintf error
~~~~
#define STRSAFE_NO_DEPRECATE 
~~~~

Edit modules/videoio/src/cap_gstreamer.cpp adding
~~~~
inline char *realpath(const char *path, char *resolved_path)
{
    return _fullpath(resolved_path,path,PATH_MAX);
}
~~~~

## GStreamer usage ##

Seems that libgstapp.dll.a is referenced as libgstapp.dll causing the missed references at videoio link time. This can be fixed acting on CMakeCache. The bug is in FindGStreamerWindows.cmake

~~~~
GSTREAMER_gstapp_LIBRARY:FILEPATH=/usr/local/mxe/usr/x86_64-w64-mingw32.shared.posix/lib/libgstapp-1.0.dll.a
~~~~


## IPP Issue ##
Pushed as PR on OpenCV: https://github.com/opencv/opencv/pull/9417

1) Lack of RunTmChk due to cmake/OpenCVFindIPP.cmake
2) Missing library of ippicv

Issue 1: The patch at http://code.opencv.org/issues/1906 provides some insights of the involved functions.The library RunTmChk provides __security_cookie and _chkstk, and it can be found online (e.g. https://github.com/dblock/dotnetinstaller/blob/master/ThirdParty/Microsoft/Visual%20Studio%208/VC/lib/RunTmChk.lib). In the past it was provided with Windows SDK. 

Solution: use the stub RunTmChk provided in the next seeciton

Issue 2: the provided file is in VS naming instead of MINGW32 naming
Solution: copy 3rdparty/ippicv/ippicv_win/lib/intel64/ippicvmt.lib to 3rdparty/ippicv/ippicv_win/lib/intel64/libippicvmt.a




## RunTmChk Stub ##

Build the following and copy to mxe lib folder

~~~~
add_library(RunTmChk STATIC code.c)
~~~~

~~~~
void __fastcall __GSHandlerCheck() {}
void __fastcall __security_check_cookie(unsigned* p) {}
void __fastcall __chkstk() {}
unsigned* __security_cookie;
~~~~

