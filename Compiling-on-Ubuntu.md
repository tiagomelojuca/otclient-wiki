```bash
  # install requeried dev packages
  sudo apt-get install build-essential cmake git-core libboost-all-dev
  sudo apt-get install libphysfs-dev libgmp3-dev liblua5.1-dev libglu1-mesa-dev libgl1-mesa-dev

  # install yaml 2.6
  wget http://yaml-cpp.googlecode.com/files/yaml-cpp-0.2.6.tar.gz
  tar xzvf yaml-cpp-0.2.6.tar.gz 
  cd yaml-cpp
  cmake .
  make
  sudo make install

  # clone, build and run
  git clone git://github.com/edubart/otclient.git
  cd otclient
  cmake .
  make
  ./otclient
```
