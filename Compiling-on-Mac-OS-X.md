This is how we compile otclient on Mac OS X, we use XQuartz to compile and run otclient, which is an X11 implementation for Mac OS, we do not use the native Cocoa API. This means that users will need XQuartz installed too to run the client. You will need to know the basics of how using the terminal in Mac OS to follow this tutorial.

## Requirements
* Mac OS X 10.6 or higher
* [XCode](https://developer.apple.com/xcode/) 
* Command Line Tools for Xcode (install them inside the XCode menu)
* [XQuartz](http://xquartz.macosforge.org/landing/)
* [Homebrew](http://mxcl.github.com/homebrew/)

You should install all those requirements first, in order, I will not cover how to install them in this tutorial.

## Installing needed libraries

We use brew to install most of the required libraries by using the following commands:

```
brew install \
  boost@1.59 \
  cmake \
  git \
  glew \
  libogg \
  libvorbis \
  lua@5.1 \
  physfs
```

## Cloning and compiling

You may need to change the included directory of your installed version of OpenSSL. Check your installed version with `brew info openssl`. If it is not version 1.0.2.n, change the version in the `cmake` command below.

```
git clone git://github.com/edubart/otclient.git
cd otclient
mkdir build
cd build
cmake \
  -DUSE_STATIC_LIBS=OFF \
  -DLUA_LIBRARY=/usr/local/Cellar/lua@5.1/5.1.5_8/lib/liblua.5.1.5.dylib \
  -DLUA_INCLUDE_DIR=/usr/local/Cellar/lua@5.1/5.1.5_8/include/lua5.1/ \
  -DBoost_INCLUDE_DIR=/usr/local/Cellar/boost@1.59/1.59.0/include/ \
  -DOPENSSL_INCLUDE_DIR=/usr/local/Cellar/openssl/1.0.2t/include/ \
  ..
make -j$(sysctl -n hw.ncpu)
```

Now you can run, the otclient output binary should be in the same directory.