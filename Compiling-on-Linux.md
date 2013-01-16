### Ubuntu

First install required development packages using apt-get

```sh
sudo apt-get install build-essential cmake git-core
sudo apt-get install libboost1.48-all-dev libphysfs-dev libssl-dev liblua5.1-dev
sudo apt-get install libglew1.6-dev libvorbis-dev libopenal-dev libz-dev
```

Get the sources, compile and run

```sh
git clone git://github.com/edubart/otclient.git
cd otclient
mkdir build && cd build
cmake ..
make
./otclient
```

### Arch Linux

The project creator @edubart uses Arch Linux at home and maintains an [AUR package for otclient](http://aur.archlinux.org/packages.php?ID=49101), make sure that you have yaourt and just run:

```sh
yaourt -S otclient-git
```