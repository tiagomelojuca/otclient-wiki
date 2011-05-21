```bash
  # install requeried dev packages
  sudo apt-get install build-essential cmake git-core libboost-all-dev
  sudo apt-get install libphysfs-dev libgmp3-dev liblua5.1-dev libglu1-mesa-dev libgl1-mesa-dev

  # clone, build and run
  git clone git://github.com/edubart/otclient.git
  cd otclient
  cmake .
  make
  ./otclient
```
