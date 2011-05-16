```bash
  # install required packages
  sudo apt-get install build-essential cmake gcc-mingw32 git-core

  # download and install required libs
  wget http://cloud.github.com/downloads/edubart/otclient/otclient-libs_mingw32-sjlj.tar.gz
  sudo tar -C /usr/i586-mingw32msvc -xzf otclient-libs_mingw32-sjlj.tar.gz

  # clone
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
