NOTE: **gcc 4.6** or greater is required to compile, it is the default gcc version in Ubuntu 11.10
```bash
  # install requeried dev packages
  sudo apt-get install build-essential cmake git-core libboost-all-dev
  sudo apt-get install libphysfs-dev libgmp3-dev liblua5.1-dev libglu1-mesa-dev libgl1-mesa-dev

  # clone, build and run
  git clone git://github.com/edubart/otclient.git
  git submodule init && git submodule update
  cd otclient
  cmake .
  make
  ./otclient
```
