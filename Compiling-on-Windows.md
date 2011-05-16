## Compiling using DOS prompt
Follow these steps to compile the otclient using Mingw32, CMake and DOS prompt command:

* Download the [latest automated mingw32  installer](http://sourceforge.net/projects/mingw/files/Automated%20MinGW%20Installer/mingw-get-inst/)
* Run and install it, when installing make sure that you enable `C++ compiler`
* Install the [latest cmake Win32 installer](http://www.cmake.org/cmake/resources/software.html)
* Now you have to add cmake and mingw32 paths to your system environment, follow this steps:
   * If you use Windows XP go into `Control Panel->System->Advanced->Environment Variables`
   * Add a new user variable named `Path`
   * Set its value to `C:\MinGW\bin;C:\MinGW\lib;C:\MinGW\include;C:\Program Files\CMake 2.8\bin`
   * You might change the above value with your correct mingw32 and cmake installation folder
* Download the [latest otclient required libraries](http://cloud.github.com/downloads/edubart/otclient/otclient-libs_mingw32.zip)
* Extract it into `C:\MinGW`
* Download and extract [latest otclient source code](https://github.com/edubart/otclient/zipball/master)
* Run CMake GUI (Start->Programs->CMake 2.8->CMake)
* Click `Browse Source` and set it to the extracted otclient source code
* Configure the build path to where you want to place otclient.exe
* Click `Configure`, select `MinGW Makefiles` and click `Finish`
* Now if everything is ok no errors appeared
* Open DOS prompt command (Start->Run->cmd.exe->Ok)
* Navigate inside the DOS prompt to the previous configured build path using 'cd'
* Run the command `mingw32-make` and it will start to compile
* Now if no errors were found otclient.exe has been created in the current folder
* To run correctly the working dir must be the otclient soruce path, so move it to otclient source path
* Now **run it!**

## Tip: Using Qt Creator IDE
If you don't like to use the DOS prompt, you can use [Qt Creator IDE](http://qt.nokia.com/downloads/qt-creator-binary-for-windows). To do that, after doing the above steps you could open the otclient/CMakeLists.txt file in Qt Creator and compile there.