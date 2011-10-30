```bash
  # gcc 4.6 is required, install from the ppa https://launchpad.net/~ubuntu-toolchain-r/+archive/test
  sudo add-apt-repository ppa:ubuntu-toolchain-r/test
  sudo apt-get update
  sudo apt-get upgrade
  sudo apt-get install g++ gcc

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
