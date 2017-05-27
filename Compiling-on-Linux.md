### Ubuntu

First install required development packages using apt-get

```sh
sudo apt-get install -y build-essential cmake git-core
sudo apt-get install -y libboost1.58-all-dev libphysfs-dev libssl-dev liblua5.1-0-dev
sudo apt-get install -y libglew-dev libvorbis-dev libopenal-dev zlib1g-dev
```

Get the sources, compile and run

```sh
git clone git://github.com/edubart/otclient.git
cd otclient && mkdir build && cd build && cmake .. && make
./otclient
```

### Arch Linux

The project creator @edubart uses Arch Linux at home and maintains an [AUR package for otclient](http://aur.archlinux.org/packages.php?ID=49101), make sure that you have yaourt and just run:

```sh
yaourt -S otclient-git
```
### Fedora

These instructions were tested on Fedora 20. Some packages that I suggest to be installed might not actually be needed and there might be a simpler way to link in Lua, but I am not aware of it. In case of a problem, contact d33tah.

#### Install Lua 5.1 to /opt/lua5.1

```
yum-builddep lua
wget "http://www.lua.org/ftp/lua-5.1.5.tar.gz" -O- | tar zxvf -
cd lua-5.1.5
make linux
mkdir /opt/lua5.1
make INSTALL_TOP=/opt/lua5.1 install
```

#### Install needed packages

```
yum install boost boost-devel physfs physfs-devel mesa-libGLw mesa-libGL-devel glew-devel openal-devel libvorbis-devel boost-system boost-thread boost-chrono boost-filesystem
```

#### Build otclient

The final command, `make`, will take most time. If you have a multi-core processor, try `make -j$(nproc)` to speed up the build process.

```
mkdir build && cd build
cmake  -DUSE_STATIC_LIBS=OFF -DLUA_LIBRARY=/opt/lua5.1/lib/liblua.a -DLUA_INCLUDE_DIR=/opt/lua5.1/include/ ..
make
```

#### Test if it runs

```
./otclient
```