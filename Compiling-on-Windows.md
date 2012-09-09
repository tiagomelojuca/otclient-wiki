In this this toturial I will explain how you get otclient compiled and running on windows machines.

### Download what you will need

There are several tools you need to compile the project, each of which is listed next to their link here:

* [CMake](http://www.cmake.org/cmake/resources/software.html) **2.8.8 or greater**
* [CodeBlocks](http://www.codeblocks.org/downloads/26) **without MinGW, we use a newer version**
* [MinGW32](http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/) 20120426 or greater
* [otclient libraries for mingw32](https://github.com/downloads/edubart/otclient/otclient-libs_mingw32-dwarf2.zip)
* otclient source code

_**--** Make sure you install their latest versions, otherwise, things might not work._

### Install MinGW32
Note that mingw32 must be 4.6 or greater, any older mingw32 that you have already installed will not work because otclient needs C++11 features which are support only by recent compilers. Run the downloaded mingw32 installer and in the installation process **make sure that you use the latest catalog when asked and check the installation of the C++ compiler**. When finished you mingw32 must be installed in C:/MinGW

### Install CMake
Run the CMake installer, should in the installation process you get asked if you want CMake to configure your PATH variable, say no, this will be manually set in the next steps.

### Install CodeBlocks
Run the CodeBlocks installer, through which you must install MinGW as well. 

_**--** Make sure you don't install MinGW as well, otherwise things might go wrong._

### Install otclient libraries
Extract the **otclient-libs_mingw32-dwarf2.zip** into *C:/Program Files/CodeBlocks/MinGW*. This zip contains 3 folders *lib*, *include* and *bin* witch will be merged into *./MinGW/lib*, *./MinGW/include* and *./MinGW/bin*.

### Configure system PATH variable
Now that all needed tools is installed, you must configure the system **PATH** variable to make CMake find MinGW32 and the installed libraries, go to:
```
 Control Panel->System->Advanced->Environment Variables
```

Check if the user variable **PATH** exists, if not, create one, then set it to:
```
C:\Program Files\CMake 2.8\bin;C:\MinGW\bin;C:\MinGW\lib;C:\MinGW\include
```

_**--** Make sure that the user variable **PATH** exists and refers to the CMake directory properly._

### Download OTClient source code
Go to our [download page](/download.html) and download the desired OTClient source code. The directory where you place these files may not be spaced. For instance, "C:\OTClient\" is **good**, but "C:\Program Files\OTClient" isn't.

### Generate CodeBlocks Project file
Run the **CMake-gui.exe** located in **\Program Files\CMake 2.8\bin**, and specify the directory in which you just placed the OTClient source code, and where you want the project files to be built. Press configure,  select **CodeBlocks - MinGW Makefiles** as the generator, then generate the project files.

### Scripting and compiling it
Open the said generated Codeblocks Project file (**otclient.cbp**) by CMake with CodeBlocks, and script away! To compile, you must first configure the folder of MinGW32, by going to **Settings** > **Compiler And Debugger...** > **Toolchain Executables**.

**-- Make sure to copy Tibia.dat and Tibia.spr inside modules/game_tibiafiles/ folder before running the client**