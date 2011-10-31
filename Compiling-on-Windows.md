NOTE: You must use **mingw32 4.6 or greater** to compile

* Download the latest mingw32 [mingw-get installer](http://sourceforge.net/projects/mingw/files/Automated%20MinGW%20Installer/mingw-get-inst/)  and run it 
* In the installation process, make sure that you use the **latest catalog** and check **C++ compiler**, otherwise it won't install mingw32-g++ 4.6
* Install the [latest CMake](http://www.cmake.org/cmake/resources/software.html)
* Now you have to add cmake and mingw32 paths to your system environment, follow this steps:
   * Go into `Control Panel->System->Advanced->Environment Variables`
   * Add a new user variable named `PATH`
   * Set its value to `C:\Program Files\CMake 2.8\bin;C:\MinGW\bin;C:\MinGW\lib;C:\MinGW\include`
   * You might change the above value with your correct mingw32 and cmake installation folder
* Download the [latest otclient required libraries](http://cloud.github.com/downloads/edubart/otclient/otclient-libs_mingw32-dwarf2.zip)
* Extract it into `C:\MinGW`
* Download and extract [latest otclient source code](https://github.com/edubart/otclient/zipball/master)
* Run CMake GUI (Start->Programs->CMake 2.8->CMake)
* Click `Browse Source` and set it to the extracted otclient source code
* Configure the build path to the same folder
* Click `Configure`, select `CodeBlocks - MinGW Makefiles` and click `Finish`
* Now if everything is ok no errors appeared
* Click `Generate` to generate codeblocks project file
* Install the [latest CodeBlocks] (http://www.codeblocks.org/downloads/binaries)
* Go to the source folder and open otclient.cbp in CodeBlocks
* Click build
* If no errors were found otclient.exe will be in the source folder
* Make sure that you have a otclient module containing the .spr/.dat files
* Now you can **run it!**