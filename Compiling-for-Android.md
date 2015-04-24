# Setup Instructions
### 1 - Setup the Libraries/SDK/JDK
Download the following files:
* Android SDK http://developer.android.com/sdk/installing/index.html?pkg=tools
* Android NDK R10d https://developer.android.com/tools/sdk/ndk/index.html
* Android Libraries for armeabi-v7a http://goo.gl/NER92t
* Java JDK: http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
* Apache ANT http://ant.apache.org/bindownload.cgi

### 2 - Extract and Install
Extract and install the files downloaded.

### 3 - Copy the Android Libraries
Put the android libraries inside the android ndk folder.

### 4 - Copying the libSDL2.so file
Put the "libSDL2.so" file inside the android/project/libs/armeabi-v7a

### 5 - Create Environment Variables:
- ANDROID_SDK pointing to the android sdk folder
- ANDROID_NDK pointing to the android ndk folder
- JAVA_HOME pointing to the java folder
- ANT_HOME pointing to the apache ant folder

### 6 - Add folders to your system path variable:
- ANDROID_NDK
- ANDROID_SDK/platform-tools (to use adb)
- ANDROID_SDK/tools (to use android)
- JAVA_HOME/bin
- ANT_HOME/bin

### 7 - Download and install cmake

### 8 - Clone the Mobile OTClient sources
`git clone -b mobile_port https://github.com/edubart/otclient.git otclient-mobile`

or simply

`git checkout mobile_port` from within the otclient git repository.

# Compiling
### 9 - Connect a Phone
Must connect a phone that with a armeabi-v7a processor.

## 10 - Run Compilation Script
**Windows:**<br/>
Create a script following the "compile_android.sh" logic (we can add one soon).<br/>
**Linux:**<br/>
Run compile_android.sh script.<br/>

Lastly contribute to the project! ;)