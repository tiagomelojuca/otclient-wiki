This is how we compile otclient on Mac OS X, we use XQuartz to compile and run otclient, which is a X11 implementation for Mac OS, we do not use the native Cocoa API. This means that users will need XQuartz installed too to run the client. You will need to know the basics on how using terminal in Mac OS to follow this tutorial.

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
brew install git
brew install cmake
brew install boost@1.59
brew install glew
brew install physfs
brew install libogg
brew install libvorbis
```

Install LUA 5.1.5

```
curl "http://www.lua.org/ftp/lua-5.1.5.tar.gz"
tar -zxvf lua-5.1.5.tar.gz
cd lua-5.1.5
make macosx test
mkdir /opt/lua5.1
make INSTALL_TOP=/opt/lua5.1 install
```

## Cloning and compiling

You may need to change the included directory of your installed version of OPENSSL. Check your installed version with `brew info openssl`. If it is not version 1.0.2.n, change the version in the `cmake` command below.

```
git clone git://github.com/edubart/otclient.git
cd otclient
mkdir build
cd build
cmake \
  -DUSE_STATIC_LIBS=OFF \
  -DLUA_LIBRARY=/opt/lua5.1/lib/liblua.a \
  -DLUA_INCLUDE_DIR=/opt/lua5.1/include/ \
  -DBoost_INCLUDE_DIR=/usr/local/Cellar/boost@1.59/1.59.0/include/ \
  -DBoost_LIBRARY_DIR=/usr/local/Cellar/boost@1.59/1.59.0/lib/ \
  -DOPENSSL_INCLUDE_DIR=/usr/local/Cellar/openssl/1.0.2n/include/ \
  ..
make -j4
```

Now you can run, the otclient output binary should be in the same directory.