## 1.1 Introduction to OpenCV for Java 
## 1.1 Java版本的OpenCV介绍
As of OpenCV 2.4.4, OpenCV supports desktop Java development. This tutorial will help you install OpenCV on your desktop operating system.  
&emsp;&emsp;自OpenCV 2.4.4开始，OpenCV开始支持桌面版Java开发。本手册将会帮助你在桌面版操作系统上安装OpenCV。
## 1.2 Install the latest Java version
## 1.2 安装最新版本的Java
Download the latest Java JDK from the [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) website. Now you should be able to install the last Java JDK by opening
the file just downloaded.  
&emsp;&emsp;从 [Oracle网站](https://www.oracle.com/java/technologies/javase-downloads.html) 下载最新的Java JDK工具包，然后打开下载好的文件安装最新的Java JDK工具包。
## 1.3 Install the latest Eclipse version
## 1.3 安装最新版本的Eclipse
Download the latest Eclipse version at the [Eclipse Download page](https://www.eclipse.org/downloads/packages/) choosing the **Eclipse IDE for Java Developers** version (suggested).  
&emsp;&emsp;在[Eclipse 下载页](https://www.eclipse.org/downloads/packages/) 选择并下载最新的**Eclipse IDE for Java Developers** 版本 (推荐)。 
  
Extract the downloaded compressed file and put the resulting folder wherever you want to. You don’t need to install anything. Alternatively, you can try the Eclipse installer.  
&emsp;&emsp;解压下载好的压缩文件并保存解压得到的文件夹。你不需要安装任何东西。或者，你也可以尝试Eclipse安装程序。
## 1.4 Install OpenCV 3.x under Windows     
## 1.4 Windows下安装OpenCV 3.x
First of all you should download the OpenCV library (version 3.x) from [here](https://opencv.org/releases/).  
&emsp;&emsp;首先从[这里](https://opencv.org/releases/)下载OpenCV库（3.x版本）。  

Then, extract the downloaded OpenCV file in a location of your choice. Once you get the folder **opencv** put in wherever you prefer.  
&emsp;&emsp;然后解压已下载的OpenCV文件到你选择的位置并保存解压后的**opencv**文件夹。  
  
Now the only two things that you will need are: the **opencv-3xx.jar** file located at **\opencv\build\java** and the **opencv_java3xx.dll** library located at **\opencv\build\java\x64** (for 64-bit systems) or **\opencv\build\java\x86** (for 32-bit systems). The _3xx_ suffix of each file is a shortcut for the current OpenCV version, e.g., it will be _300_ for OpenCV 3.0 and _330_ for OpenCV 3.3.  
&emsp;&emsp;接下来你只需要两份文件：位于\opencv\build\java的opencv-3xx.jar文件以及位于\opencv\build\java\x64的opencv_java3xx.dll库（64位系统）或位于\opencv\build\java\x8的opencv_java3xx.dll库（32位系统）。每份文件名称中的*3xx*后缀都是关于当前OpenCV版本的快捷方式。例如，对于OpenCV 3.0后缀为*300*；对于OpenCV 3.3后缀为*330*。
## 1.5 Install OpenCV 3.x under macOS  
## 1.5 macOS下安装OpenCV 3.x
The quickest way to obtain OpenCV under macOS is to use [Homebrew](https://brew.sh/). After installing Homebrew, you have to check whether the _XCode Command Line Tools_ are already installed on your system.  
&emsp;&emsp;macOS下安装OpenCV最快的方法就是使用[Homebrew](https://brew.sh/)。Homebrew安装完毕之后，必须检查你的系统是否已经安装了*XCode命令行工具*。
  
To do so, open the Terminal and execute: **xcode-select --install** If macOS asks for installing such tools, proceed with the download and installation. Otherwise, continue with the OpenCV installation.  
&emsp;&emsp;为此，打开终端并执行**xcode-select --install**。如果macOS要求安装此类工具，则下载并安装*XCode命令行工具*。否则继续安装OpenCV。
    
As a prerequisite, check that Apache Ant is installed. Otherwise, install it with Homebrew: **brew install ant**. Ant should be available at **/usr/local/bin/ant**.  
&emsp;&emsp;请确认安装OpenCV必备的Apache Ant已经安装完毕。否则，请通过Homebrew: **brew install ant**安装。同时，Apache Ant应当保存在 **/usr/local/bin/ant**。  

To install OpenCV (with Java support) through Homebrew, you need to edit the _opencv_ formula in Homebrew, to add support for Java: **brew edit opencv** In the text editor that will open, change the line:**-DBUILD_opencv_java=OFF in -DBUILD_opencv_java=ON** then, after saving the file, you can effectively install OpenCV: **brew install --build-from-source opencv**  
&emsp;&emsp;为了使用Homebrew来安装Java版本的OpenCV，你需要在Homebrew中编辑opencv的公式来添加对Java版本的支持：**brew edit opencv**。打开文本编辑器，修改以下行：**-DBUILD_opencv_java=OFF in -DBUILD_opencv_java=ON**。保存文件后，即可安装OpenCV：**brew install --build-from-source opencv**。  

After the installation of OpenCV, the needed jar file and the dylib library will be located at **/usr/local/Cellar/opencv/3.x.x/share/OpenCV/java/**, e.g., **/usr/local/Cellar/opencv/3.3.1/share/OpenCV/java/**.  
&emsp;&emsp;OpenCV完成安装后，所需的jar文件和dylib库将位于 **/usr/local/Cellar/opencv/3.x.x/share/OpenCV/java/** （比如/usr/local/Cellar/opencv/3.3.1/share/OpenCV/java/）。

Please, notice that this method doesn’t work if you update OpenCV from a previous version: you need to uninstall OpenCV and install it again.  
&emsp;&emsp;请注意：如果你是将OpenCV从较早版本更新到最新版本的，此方法无效！你需要卸载原有的OpenCV并重新安装。
## 1.6 Install OpenCV 3.x under Linux   
## 1.6 Linux下安装OpenCV 3.x
Please, note: the following instructions are also useful if you want to compile OpenCV under Windows or macOS. Linux package management systems (_apt-get, yum, etc._) may provide the needed version of the OpenCV library.  
&emsp;&emsp;请注意：以下教程同样适用于在Windows或macOS下编译OpenCV。Linux软件包管理系统（_apt-get_、*yum*等）可以提供OpenCV库的所需版本。

As first step, download and install [CMake](https://cmake.org/download/) and [Apache Ant](http://ant.apache.org/), if you don’t have any of these. Download the OpenCV library from [its website](https://opencv.org/releases/). Extract the downloaded OpenCV file in a location of your choice and open CMake ( cmake-gui ). Put the location of the extracted OpenCV library in the **Where is the source code field** (e.g.,/opencv/) and insert the destination directory of your build in the **Where to build the binaries field** (e.g.,/opencv/build). At last, check the **Grouped** and **Advanced** checkboxes.  
&emsp;&emsp;第一步，下载并安装[CMake](https://cmake.org/download/)和[Apache Ant](http://ant.apache.org/)。  
&emsp;&emsp;第二步，下载OpenCV库，下载地址为[OpenCV库网站](https://opencv.org/releases/)。  
&emsp;&emsp;第三步，解压缩已下载的OpenCV文件到你选好的位置，并打开CMake（cmake-gui）。  
&emsp;&emsp;第四步，在 **“Where is the source code field”** 输入解压出来的OpenCV库所在位置（例如/opencv/）；在 **“Where to build the binaries field”** 插入构件的目的目录（例如/opencv/build)。  
&emsp;&emsp;最后，选中复选框“Grouped”、“Advanced”。  
  
 ![UC6u2d.png](https://s1.ax1x.com/2020/07/06/UC6u2d.png)  
   
 Now press **Configure** and use the default compilers for **Unix Makefiles**. Please, be sure to have installed a C/C++ compiler. In the Ungrouped Entries group, insert the path to the Apache Ant executable (e.g., **/apache-ant-1.9.6/bin/ant**). In the **BUILD** group, unselect:  
 &emsp;&emsp;现在按下 **“Configure”** 并使用**Unix Makefiles**的默认编译器。务必确认已经安装C/C++编译器。在 **“Ungrouped Entries”** 组，插入路径到Apache Ant可执行文件（比如**/apache-ant-1.9.6/bin/ant**）。在 **“BUILD”** 组，取消选择：   
 
 • **BUILD_PERF_TESTS**  
 • **BUILD_PERF_TESTS** 
 
 • **BUILD_SHARED_LIBRARY** to make the Java bindings dynamic library all-sufficient   
 •使动态库完全绑定于Java
 
 • **BUILD_TESTS**  
 • **BUILD_TESTS**  
 
 • **BUILD_opencv_python**  
 • **BUILD_opencv_python**  
 
 In the **CMAKE** group, set to **Debug** (or Release) the **CMAKE_BUILD_TYPE**  
 &emsp;&emsp;在“**CMAKE**”组，开始“Debug”（或“Release”）**“CMAKE_BUILD_TYPE”**。
 
 In the **JAVA** group:  
&emsp;&emsp;在**Java**组：  

 • insert the Java AWT include path (e.g., **/usr/lib/jvm/java-1.8.0/include/**)  
 •  插入Java AWT包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/** ）；
 
 • insert the Java AWT library path (e.g.,  **/usr/lib/jvm/java-1.8.0/include/jawt.h** )  
 • 插入Java AWT库路径（例如 **/usr/lib/jvm/java-1.8.0/include/jawt.h** ）； 
 
 • insert the Java include path (e.g.,  **/usr/lib/jvm/java-1.8.0/include/** )  
 •插入Java包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/** ）；  
 
 • insert the alternative Java include path (e.g., **/usr/lib/jvm/java-1.8.0/include/linux**)  
 • 插入备用Java包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/linux** ）；
 
 • insert the JVM library path (e.g., **/usr/lib/jvm/java-1.8.0/include/jni.h**)  
 • 插入JYM库路径（例如 **/usr/lib/jvm/java-1.8.0/include/jni.h** ）。
 
 Press **Configure** twice, and the CMake window should appear with a white background. If not, fix the red lines and press **Configure** again. Now, press **Generate** and close CMake.   
 &emsp;&emsp;连按两次 **“Configure”** ，CMake窗口应显示为白色背景。否则的话，请修复红线，并再按一次 **“Configure”** 。接下来，请按 **“Generate”** 并关闭CMake。  
 
 ![UCcFzj.png](https://s1.ax1x.com/2020/07/06/UCcFzj.png)  
  
 Now open the terminal, go to the **build** folder of OpenCV and compile everything with the command: **make-j**. Notice that the _-j_ flag tells _make_ to run in parallel with the maximum number of allowed job threads, which makes the build theoretically faster. Wait for the process to be completed... If everything went well you should have **opencv-3xx.jar** in the **/opencv/build/bin** directory and **libopencv_java3xx.so** in the **/opencv/build/lib** directory. The _3xx_ suffix of each file is a shortcut for the current OpenCV version, e.g., it will be _300_ for OpenCV 3.0 and _330_ for OpenCV 3.3. This is everything you need.  
 &emsp;&emsp;现在打开终端，转到OpenCV的**build**文件夹，并使用命令**make-j**编译所有内容。  
 &emsp;&emsp;请注意：*-j*标记指示*make*运行允许工作的最大线程数，理论上加快了构件速度。   
 &emsp;&emsp;等待过程完成…  
 &emsp;&emsp;若一切运行顺利，在目录/opencv/build/bin中你将得到opencv-3xx.jar，在目录/opencv/build/lib中你将得到libopencv_java3xx.so。同样地，每份文件名称中的*3xx*后缀都是关于当前OpenCV版本的快捷方式。例如，对于OpenCV 3.0后缀为*300*；对于OpenCV 3.3后缀为*330*。  
 &emsp;&emsp;以上就是你安装时所需要的一切。
## 1.7 Set up OpenCV for Java in Eclipse  
## 1.7 Eclipse中安装Java版本的OpenCV
 Open Eclipse and select a workspace of your choice. Create a User Library, ready to be used on all your next projects:go to **Window > Preferences....**  
&emsp;&emsp;打开Eclipse，选择用户空间。创建用户库，该库应可以支持接下来要创建的所有新项目。转到：**Window > Preferences....**。  
 
 ![UCgx58.png](https://s1.ax1x.com/2020/07/06/UCgx58.png)  
  
 From the menu navigate under **Java > Build Path > User Libraries** and choose **New....** Enter a name for the library (e.g., opencv) and select the newly created user library. Choose **Add External JARs...**, browse to select **opencv-3xx.jar** from your computer. After adding the jar, extend it, select **Native library location** and press **Edit....**  
&emsp;&emsp;从菜单导航到**Java > Build Path > User Libraries**下，选择**New....**。键入库名（比如opencv），然后选择最近创建的用户库。点击**Add External JARs...**，从电脑中浏览并选择**opencv-3xx.jar**。添加完毕后，扩展文件，选择**Native library location**并点击**Edit....**。 
  
 ![UC2Cvj.png](https://s1.ax1x.com/2020/07/06/UC2Cvj.png)  
  
 Select **External Folder...** and browse to select the folder containing the OpenCV libraries (e.g.,**C:\opencv\build\java\x64** under Windows).  
&emsp;&emsp;选择**External Folder...**，从电脑中浏览并选择包含OpenCV库的文件夹（例如Windows下的**C:\opencv\build\java\x64**）。  
   
 In case of MacOS, if you installed OpenCV _without_ Homebrew, you need to create a soft link with .dylib extension for
 the .so file. E.g., from the terminal, type: **ln -s libopencv_java300.so libopencv_java300.dylib**  
&emsp;&emsp;MacOS下，如果你*不是通过*Homebrew安装OpenCV的，则需要为.so文件创建一个软连接，连接扩展名为.dylib。例如，从终端输入**ln -s libopencv_java300.so libopencv_java300.dylib**。 
 
## 1.8 Set up OpenCV for Java in other IDEs (experimental)  
## 1.8 其他IDE（实验版本）中安装Java版本的OpenCV 
 If you are using IntelliJ, you can specify the location of the library with the VM argument **-Djava.library.path=/opencv/build/lib**.  
&emsp;&emsp;如果你正在使用的是IntelliJ，可以通过VM参数-Djava.library.path=/opencv/build/lib指定库的位置。

 