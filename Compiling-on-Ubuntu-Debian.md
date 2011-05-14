```bash
  # install requeried dev packages
  sudo apt-get install build-essential cmake libboost-dev-all
  sudo apt-get install libphysfs-dev libgmp3-dev liblua5.1-dev libglu1-mesa-dev libgl1-mesa-dev

  # install yaml 2.6
  wget http://yaml-cpp.googlecode.com/files/yaml-cpp-0.2.6.tar.gz
  tar xzvf yaml-cpp-0.2.6.tar.gz 
  cd yaml-cpp
  cmake .
  make
  sudo make install
  cd ..

  # clone repository
  git clone git://github.com/edubart/otclient.git
  cd otclient

  # building
  mkdir build
  cd build
  cmake ..
  cd ..
  make -C build

  # running
  ./build/otclient
```
