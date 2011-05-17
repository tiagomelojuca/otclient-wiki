## Compiling using DOS prompt
Follow these steps to compile the otclient using Mingw32, CMake and DOS prompt command:

* Download and install the [latest codeblocks mingw32 setup](http://sourceforge.net/projects/codeblocks/files/Binaries/10.05/Windows/codeblocks-10.05mingw-setup.exe)
* Install the [latest cmake Win32 installer](http://www.cmake.org/cmake/resources/software.html)
* Now you have to add cmake and mingw32 paths to your system environment, follow this steps:
   * If you use Windows XP go into `Control Panel->System->Advanced->Environment Variables`
   * Add a new user variable named `PATH`
   * Set its value to `C:\Program Files\CMake 2.8\bin;C:\Program Files\CodeBlocks\MinGW\bin;C:\Program Files\CodeBlocks\MinGW\lib;C:\Program Files\CodeBlocks\MinGW\include`
   * You might change the above value with your correct mingw32 and cmake installation folder
* Download the [latest otclient required libraries](http://cloud.github.com/downloads/edubart/otclient/otclient-libs_mingw32-sjlj.zip)
* Extract it into `C:\Program Files\CodeBlocks\MinGW`
* Download and extract [latest otclient source code](https://github.com/edubart/otclient/zipball/master)
* Run CMake GUI (Start->Programs->CMake 2.8->CMake)
* Click `Browse Source` and set it to the extracted otclient source code
* Configure the build path to the same folder
* Click `Configure`, select `CodeBlocks - MinGW Makefiles` and click `Finish`
* Now if everything is ok no errors appeared
* Click `Generate`
* Go to the source folder and open otclient.cbp in CodeBlocks
* Click build
* Iif no errors were found otclient.exe has been created into the source folder
* Now you can **Run it!**