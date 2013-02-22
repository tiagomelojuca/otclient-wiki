This is how we compile otclient on Mac OS X, we use XQuartz to compile and run otclient, which is a X11 implementation for Mac OS, we do not use the native Cocoa API. This means that users will need XQuartz installed too to run the client. You will need to know the basics on how using terminal in Mac OS to follow this tutorial.

## Requirements
* Mac OS X 10.6 or higher
* [XCode](https://developer.apple.com/xcode/) 
* Command Line Tools for Xcode (install them inside the XCode menu)
* [XQuartz](http://xquartz.macosforge.org/landing/)
* [Homebrew](http://mxcl.github.com/homebrew/)

You should install all those requirements first, in order, I will not cover how to install them in this tutorial.

## Installing needed libraries

We use brew to install most of required libraries by using the following commands:

```
brew install git
brew install cmake
brew install lua
brew install boost
brew install glew
brew install physfs
brew install libogg
brew install libvorbis
```

## Cloning and compiling 

```
git clone git://github.com/edubart/otclient.git
cd otclient
mkdir build
cd build
cmake ..
make -j4
```

Now you can run, the otclient output binary should be in the same directory.