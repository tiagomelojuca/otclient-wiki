In this this toturial I will explain how you get otclient compiled and running on windows machines.

### Download what you will need

First downloaded need tools, the following links points to their download pages, make sure to download the latest versions otherwise you might fail in the next steps.

* [MinGW32 installer](http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/) **20120426 or greater**
* [CMake](http://www.cmake.org/cmake/resources/software.html) **2.8.8 or greater**
* [QtCreator standalone IDE](http://qt.nokia.com/downloads/qt-creator-binary-for-windows) **2.5.0 or greater**
* [otclient libraries for mingw32](https://github.com/downloads/edubart/otclient/otclient-libs_mingw32-dwarf2.zip)
* otclient source code

### Install MinGW32

Note that mingw32 must be 4.6 or greater, any older mingw32 that you have already installed will not work because otclient needs C++11 features which are support only by recent compilers.
Run the downloaded mingw32 installer and in the installation process **make sure that you use the latest catalog when asked** and **check the installation of the C++ compiler**. When finished
you mingw32 must be installed in C:/MinGW

### Install CMake
Run the cmake installer, in the installation process you will be asked if you want that cmake configure your PATH variable, say no, this will be manually set in the next steps.

### Install QtCreator
Just run qtcreator installer. Note that this tutorial uses the standalone IDE which comes without a compiler. If you have a previuosly installed QtCreator SDK (which already comes with MingW32) then you will have to change the compiler in the QtCreator options to the new installed version of MinGW32.

### Install otclient libraries
Extract the **otclient-libs_mingw32-dwarf2.zip** into *C:/MinGW*. This zip contains 3 folders *lib*, *include* and *bin* witch will be merged into *C:/MinGW/lib*, *C:/MinGW/include* and *C:/MinGW/bin*.

### Configure system PATH variable
Now that all needed tools is installed, you must configure the system **PATH** variable to make CMake find MinGW32 and the installed libraries, go to:
```
 Control Panel->System->Advanced->Environment Variables
```
Check if the user variabe **PATH** exists, if not, create one, then set it to:

```
C:\Program Files\CMake 2.8\bin;C:\MinGW\bin;C:\MinGW\lib;C:\MinGW\include
```

Make sure that these paths exists and matchs witch the installed ones.

### Download otclient source code
Go to our [download page](/download.html) and download the desired otclient source code.

### Compile it
Open CMakeLists.txt found inside otclient source code folder in QtCreator, a box will appears asking for cmake configuration, just click generate,
if no errors appeared everything is ok and now you can click the build button. Compilation will take a few minutes (because of mingw32 issues compilation on windows is slow).

### Run it
Before running copy Tibia.dat and Tibia.spr inside modules/game_tibiafiles/ folder, now run!