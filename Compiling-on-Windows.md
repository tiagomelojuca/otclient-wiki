In this this tutorial I will explain how you get otclient compiled and running on windows machines.

# Miscrosoft Visual Studio 2013

### Download MSVC 2013
Download the latest [Miscrosoft Visual Studio](https://www.visualstudio.com/) and install it.
Or download it from
[Mediafire](http://www.mediafire.com/file/az4y6skk76ucebq/en_visual_studio_community_2013_with_update_5_x86_6816332.exe)


### Download OTClient source code
Download the latest [OTClient sources](https://github.com/edubart/otclient/archive/master.zip). The directory in which you place the source files may not contain any spaces (e.g. "C:\OTClient\" is **good**, however "C:\Program Files\OTClient" is not).

### Download OTClient Extra Libraries
[OTClient libraries](https://mega.nz/#!1Zg0jK6Q!gA5jHmL4qU92XnDdy98UfS2y1KFQQvbjS_L5p5UHDYk).
Or from [Mediafire](http://www.mediafire.com/file/vip38k1uy7eagk0/otclient-msvc13-libs.zip)
Extract the otclient libraries in the **C** directory

Download [Boost Version 1.55.0](http://www.boost.org/users/history/version_1_55_0.html)
or you can download it from [Mediafire](http://www.mediafire.com/file/pn3ibrnphddw28x/boost_1_55_0.zip)
then extract and place it in the **otclient-msvc13-libs** directory.

_For now, those libraries are the same as the ones required when compiling with MinGW, although not all of it will be used or required._

### Open OTClient source code on MVSCV
Go to OTClient sources \vc12 and right click the **sln** file and select open with **Mircosoft Visual Studio 2013**.

At the top of the screen to the right of where it says **Local Windows Debugger**, make sure **Release** is selected as your _solution configuration_ & to the right of that make sure **Win32** is selected as your _solution platform_.

### Configuring Libraries and Includes
Right click the project select **properties** then go to **VC++ Directories** then select the **Include Directories**, select all the text in the box and replace with this.
```
C:\otclient-msvc13-libs\libogg-1.3.1\include;C:\otclient-msvc13-libs\libvorbis-1.3.3\include;C:\otclient-msvc13-libs\physfs-2.0.3\include;C:\otclient-msvc13-libs\OpenSSL-1.0.1e\include;C:\otclient-msvc13-libs\zlib-1.2.5\include;C:\otclient-msvc13-libs\OpenAL\include\AL;C:\otclient-msvc13-libs\glew-1.10.0\include;C:\otclient-msvc13-libs\LuaJIT-2.0.2\include;C:\otclient-msvc13-libs\boost_1_55_0\include;..\src;$(IncludePath)
```

Then select the **Library Directories** and select all the text in the box and replace that with this.
```
C:\otclient-msvc13-libs\libogg-1.3.1\lib;C:\otclient-msvc13-libs\libvorbis-1.3.3\lib;C:\otclient-msvc13-libs\physfs-2.0.3\lib;C:\otclient-msvc13-libs\OpenSSL-1.0.1e\lib\VC;C:\otclient-msvc13-libs\zlib-1.2.5\lib;C:\otclient-msvc13-libs\OpenAL\lib;C:\otclient-msvc13-libs\LuaJIT-2.0.2\lib;C:\otclient-msvc13-libs\glew-1.10.0\lib;C:\otclient-msvc13-libs\boost_1_55_0\lib;$(LibraryPath)
```
Let it load the additional libraries, when it says **Ready** in the left hand bottom corner of the screen. The project is ready to be compiled.

### Compiling
To compile go to **Build** in the main menu > **Build Solution**.

In the end you may see link warnings such as.
```
1>libvorbisfile_static.lib(vorbisfile.obj) : warning LNK4204: 'C:\OTClient\vc12\Release\vc120.pdb' is missing debugging information for referencing module; linking object as if no debug info
```
Its really nothing to be concerned with, as long as you see this message, you are good to go.

`========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========`

Once it has compiled, take the **otclient.exe** from the **vc12\Release** directory and place it in the root directory (root is the directory with **init.lua**) and unzip these dll's in the root directory as well.
[OtClient DLL's](http://www.mediafire.com/file/uzs12tdk4bln29s/otclient_dlls.zip)

### Scripting
Open the code of the project and script away! 

**Make sure to copy Tibia.dat and Tibia.spr inside /data/things/<version>/ folder before running the client**

### Known Problems

#### unistd.h
It is possible that you'll have problems with <unistd.h>, which is a library from MinGW. The easy turnaround for that is to create you'r own unistd.h. For that you'll need to download [getopt.cpp](https://gist.github.com/ashelly/7776712) and create an unistd.h file with the following [code](http://stackoverflow.com/questions/341817/is-there-a-replacement-for-unistd-h-for-windows-visual-c).

Change:
```
    typedef __int8            int8_t;
    typedef __int16           int16_t;
    typedef __int32           int32_t;
    typedef __int64           int64_t;
    typedef unsigned __int8   uint8_t;
    typedef unsigned __int16  uint16_t;
    typedef unsigned __int32  uint32_t;
    typedef unsigned __int64  uint64_t;
```

To:
```
    typedef signed __int8            int8_t;
    typedef signed __int16           int16_t;
    typedef signed __int32           int32_t;
    typedef signed __int64           int64_t;
    typedef unsigned __int8   uint8_t;
    typedef unsigned __int16  uint16_t;
    typedef unsigned __int32  uint32_t;
    typedef unsigned __int64  uint64_t;
```

Finally, add the folder with getopt.cpp and your new unistd.h to Visual Studio in the same way you did with the 'OTClient Extra Libraries'.

#### OpenAL error, from '\src\framework\sound\declarations.h'
It is possible that the only problem is the missing AL/, so change:

```
    #include <al.h>
    #include <alc.h>
```

To:

```
    #include <AL/al.h>
    #include <AL/alc.h>
```

# Codeblocks
### Download what you will need

There are several tools you need to compile the project, each of which is listed next to their link here:

* [CMake](http://www.cmake.org/cmake/resources/software.html) **2.8.8 or greater**
* [CodeBlocks](http://www.codeblocks.org/downloads/26) **without MinGW, we use a newer version**
* [MinGW32](http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/) 20120426 or greater
* [otclient libraries for mingw32](https://mega.nz/#!1Zg0jK6Q!gA5jHmL4qU92XnDdy98UfS2y1KFQQvbjS_L5p5UHDYk)
* otclient source code

_Make sure you install their latest versions, otherwise, things might not work._
_Note we will be using C:/MinGW as our the toolchain directory, you can change it to your liking but care for conflicts._

### Install MinGW32
Note that GCC must be 4.6 or greater, any older GCC that you have already installed will not work because otclient needs C++11 features which are supported only by recent compilers. Run the downloaded **MinGW32** installer and in the installation process **make sure that you use the latest catalog when asked and check the installation of the C++ compiler**. When finished your MinGW should be installed in C:/MinGW.
_Note it's safer to install the MSYS system and work with it.[citiation needed]._

### Install CMake
Run the CMake installer, should in the installation process you get asked if you want CMake to configure your PATH variable, say no, this will be manually set in the next steps.

### Install CodeBlocks
Run the CodeBlocks installer, _Remember, do ***NOT*** install MinGW when it asks.

### Install otclient libraries
Extract the **otclient-libs_mingw32-dwarf2.zip** into *C:/MinGW/. This zip contains 3 folders *lib*, *include* and *bin* which will be merged into *C:/MinGW/lib*, *C:/MinGW/include* and *C:/MinGW/bin*.

### Configure system PATH variable
Now that all needed tools is installed, you must configure the system **PATH** variable to make CMake find MinGW32 and the installed libraries, go to:
```
 Control Panel->System->Advanced->Environment Variables
```

Check if the user variable **PATH** exists, if not, create one, then set it to:
```
C:\Program Files (x86)\CMake 2.8\bin;C:\MinGW\bin;C:\MinGW\lib;C:\MinGW\include
```

_Make sure that the user variable **PATH** exists and refers to the CMake directory properly._

### Download OTClient source code
Download the latest [OTClient sources](https://github.com/edubart/otclient/archive/master.zip). The directory in which you place the source files may not contain any spaces (e.g. "C:\OTClient\" is **good**, however "C:\Program Files\OTClient" is not).

### Generate CodeBlocks Project file
Run the **CMake-gui.exe** located in **\Program Files\CMake 2.8\bin**, and specify the directory in which you just placed the OTClient source code, and where you want the project files to be built. Press configure,  select **CodeBlocks - MinGW Makefiles** as the generator, then generate the project files.

### Scripting and compiling it
Open the said generated Codeblocks Project file (**otclient.cbp**) by CMake with CodeBlocks, and script away! To compile, you must first configure the folder of MinGW32, by going to **Settings** > **Compiler And Debugger...** > **Toolchain Executables**.

**Make sure to copy Tibia.dat and Tibia.spr inside /data/things/<version>/ folder before running the client**

### Problems?
If your CodeBlocks (or CMake) complains it cannot find GCC or any working compiler, configure CodeBlock's compiler via settings there.
Any other problem should be posted in [otclient's otland forum](http://otland.net/f494/) or alternatively IRC (see README), don't spam! Ask, wait, try to solve it yourself until you get an answer, do ***NOT*** re-ask.

### Dx9 Support Layer
If you would like to enable the dx9 support layer for otclient you need to compile with *-DOPENGLES=2.0*. Now otclient.exe will ask for libEGL.dll and libGLESv2.dll which you can get [here](https://dl.dropbox.com/u/49948294/otclient/dx9_dlls.zip), place these dlls with the otclient.exe folder.