```Bash
  # install required packages
  sudo apt-get install build-essential cmake gcc-mingw32 git-core

  # download and install required libs
  cd /usr/i586-mingw32msvc
  sudo wget http://github.com/downloads/edubart/otclient/otclient-mingw32-libs.tar.gz
  sudo tar xzf otclient-mingw32-libs.tar.gz
  sudo rm otclient-mingw32-libs.tar.gz

  # clone
  cd $HOME
  git clone git://github.com/edubart/otclient.git

  # build
  cd otclient
  mkdir build.win32
  cd build.win32
  cmake .. -DCMAKE_TOOLCHAIN_FILE=../cmake/i586-mingw32msvc_toolchain.cmake
  make

  # run with wine
  cd ..
  wine build.win32/otclient.exe
```
