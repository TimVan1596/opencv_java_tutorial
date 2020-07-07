## 1.1 Introduction to OpenCV for Java 
## 1.1 Java版本的OpenCV介绍
As of OpenCV 2.4.4, OpenCV supports desktop Java development. This tutorial will help you install OpenCV on your desktop operating system.  
自OpenCV 2.4.4开始，OpenCV开始支持桌面版Java开发。本手册将会帮助你在桌面版操作系统上安装OpenCV。
## 1.2 Install the latest Java version
## 1.2 安装最新版本的Java
Download the latest Java JDK from the [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) website. Now you should be able to install the last Java JDK by opening
the file just downloaded.  
从 [Oracle网站](https://www.oracle.com/java/technologies/javase-downloads.html) 下载最新的Java JDK工具包，然后打开下载好的文件安装最新的Java JDK工具包。
## 1.3 Install the latest Eclipse version
## 1.3 安装最新版本的Eclipse
Download the latest Eclipse version at the [Eclipse Download page](https://www.eclipse.org/downloads/packages/) choosing the **Eclipse IDE for Java Developers** version (suggested).  
在[Eclipse 下载页](https://www.eclipse.org/downloads/packages/) 选择并下载最新的**Eclipse IDE for Java Developers** 版本 (推荐)。 
  
Extract the downloaded compressed file and put the resulting folder wherever you want to. You don’t need to install anything. Alternatively, you can try the Eclipse installer.  
解压下载好的压缩文件并保存解压得到的文件夹。你不需要安装任何东西。或者，你也可以尝试Eclipse安装程序。
## 1.4 Install OpenCV 3.x under Windows Windows系统下安装OpenCV 3.x
First of all you should download the OpenCV library (version 3.x) from [here](https://opencv.org/releases/).  
首先从[这里](https://opencv.org/releases/)下载OpenCV库（3.x版本）。  

Then, extract the downloaded OpenCV file in a location of your choice. Once you get the folder **opencv** put in wherever you prefer.  
然后解压已下载的OpenCV文件到你选择的位置并保存解压后的**opencv**文件夹。  
  
Now the only two things that you will need are: the **opencv-3xx.jar** file located at **\opencv\build\java** and the **opencv_java3xx.dll** library located at **\opencv\build\java\x64** (for 64-bit systems) or **\opencv\build\java\x86** (for 32-bit systems). The _3xx_ suffix of each file is a shortcut for the current OpenCV version, e.g., it will be _300_ for OpenCV 3.0 and _330_ for OpenCV 3.3.  
接下来你只需要两份文件：位于**\opencv\build\java**的**opencv-3xx.jar**文件以及位于**\opencv\build\java\x64**的**opencv_java3xx.dll**库（64位系统）或位于**\opencv\build\java\x8**的**opencv_java3xx.dll**库（32位系统）。每份文件名称中的*3xx*后缀都是关于当前OpenCV版本的快捷方式。例如，对于OpenCV 3.0后缀为*300*；对于OpenCV 3.3后缀为*330*。
## 1.5 Install OpenCV 3.x under macOS
The quickest way to obtain OpenCV under macOS is to use [Homebrew](https://brew.sh/). After installing Homebrew, you have to check whether the XCode Command Line Tools are already installed on your system.  
  
To do so, open the Terminal and execute: **xcode-select --install** If macOS asks for installing such tools, proceed with the download and installation. Otherwise, continue with the OpenCV installation.  
    
As a prerequisite, check that Apache Ant is installed. Otherwise, install it with Homebrew: **brew install ant**. Ant should be available at **/usr/local/bin/ant**.  
  
To install OpenCV (with Java support) through Homebrew, you need to edit the _opencv_ formula in Home-brew, to add support for Java: **brew edit opencv** In the text editor that will open, change the line:**-DBUILD_opencv_java=OFF in -DBUILD_opencv_java=ON** then, after saving the file, you can effectively install OpenCV: **brew install --build-from-source opencv**  

After the installation of OpenCV, the needed jar file and the dylib library will be located at **/usr/local/Cellar/opencv/3.x.x/share/OpenCV/java/**, e.g., **/usr/local/Cellar/opencv/3.3.1/share/OpenCV/java/**.  

Please, notice that this method doesn’t work if you update OpenCV from a previous version: you need to uninstall OpenCV and install it again.
## 1.6 Install OpenCV 3.x under Linux
Please, note: the following instructions are also useful if you want to compile OpenCV under Windows or macOS. Linux package management systems (_apt-get, yum, etc._) may provide the needed version of the OpenCV library.  

As first step, download and install [CMake](https://cmake.org/download/) and [Apache Ant](http://ant.apache.org/), if you don’t have any of these. Download the OpenCV library from [its website](https://opencv.org/releases/). Extract the downloaded OpenCV file in a location of your choice and open CMake ( cmake-gui ). Put the location of the extracted OpenCV library in the **Where is the source code field** (e.g.,/opencv/) and insert the destination directory of your build in the **Where to build the binaries field** (e.g.,/opencv/build). At last, check the **Grouped** and **Advanced** checkboxes.  
  
 ![UC6u2d.png](https://s1.ax1x.com/2020/07/06/UC6u2d.png)  
   
 Now press **Configure** and use the default compilers for **Unix Makefiles**. Please, be sure to have installed a C/C++ compiler. In the Ungrouped Entries group, insert the path to the Apache Ant executable (e.g., **/apache-ant-1.9.6/bin/ant**). In the **BUILD** group, unselect:  
 
 • **BUILD_PERF_TESTS**  
 
 • **BUILD_SHARED_LIBRARY** to make the Java bindings dynamic library all-sufficient  
 
 • **BUILD_TESTS**  
 
 • **BUILD_opencv_python**  
 
 In the **CMAKE** group, set to **Debug** (or Release) the **CMAKE_BUILD_TYPE**  
 
 In the **JAVA** group:  
 
 • insert the Java AWT include path (e.g., **/usr/lib/jvm/java-1.8.0/include/**)  
 
 • insert the Java AWT library path (e.g., **/usr/lib/jvm/java-1.8.0/include/jawt.h**)  
 
 • insert the Java include path (e.g., **/usr/lib/jvm/java-1.8.0/include/**)  
 
 • insert the alternative Java include path (e.g., **/usr/lib/jvm/java-1.8.0/include/linux**)  
 
 • insert the JVM library path (e.g., **/usr/lib/jvm/java-1.8.0/include/jni.h**)  
 
 Press **Configure** twice, and the CMake window should appear with a white background. If not, fix the red lines and press **Configure** again. Now, press **Generate** and close CMake.  
 ![UCcFzj.png](https://s1.ax1x.com/2020/07/06/UCcFzj.png)  
  
 Now open the terminal, go to the **build** folder of OpenCV and compile everything with the command: **make-j**. Notice that the _-j_ flag tells _make_ to run in parallel with the maximum number of allowed job threads, which makes the build theoretically faster. Wait for the process to be completed... If everything went well you should have **opencv-3xx.jar** in the **/opencv/build/bin** directory and **libopencv_java3xx.so** in the **/opencv/build/lib** directory. The _3xx_ suffix of each file is a shortcut for the current OpenCV version, e.g., it will be _300_ for OpenCV 3.0 and _330_ for OpenCV 3.3. This is everything you need.
 ## 1.7 Set up OpenCV for Java in Eclipse
 Open Eclipse and select a workspace of your choice. Create a User Library, ready to be used on all your next projects:go to **Window > Preferences....**  
 
 ![UCgx58.png](https://s1.ax1x.com/2020/07/06/UCgx58.png)  
  
 From the menu navigate under **Java > Build Path > User Libraries** and choose **New....** Enter a name for the library (e.g., opencv) and select the newly created user library. Choose **Add External JARs...**, browse to select **opencv-3xx.jar** from your computer. After adding the jar, extend it, select **Native library location** and press **Edit....**   
  
 ![UC2Cvj.png](https://s1.ax1x.com/2020/07/06/UC2Cvj.png)  
  
 Select **External Folder...** and browse to select the folder containing the OpenCV libraries (e.g.,**C:\opencv\build\java\x64** under Windows).  
   
 In case of MacOS, if you installed OpenCV _without_ Homebrew, you need to create a soft link with .dylib extension for
 the .so file. E.g., from the terminal, type: **ln -s libopencv_java300.so libopencv_java300.dylib**  
 
 ## 1.8 Set up OpenCV for Java in other IDEs (experimental)
 If you are using IntelliJ, you can specify the location of the library with the VM argument **-Djava.library.path=/opencv/build/lib**.

 