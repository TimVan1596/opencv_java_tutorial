# 第一章 Java版本OpenCV的安装  

## 1.1 Java版本的OpenCV介绍
&emsp;&emsp;自OpenCV 2.4.4开始，OpenCV开始支持桌面版Java开发。本手册将会帮助你在桌面版操作系统上安装OpenCV。
## 1.2 安装最新版本的Java
&emsp;&emsp;从 [Oracle网站](https://www.oracle.com/java/technologies/javase-downloads.html) 下载最新的Java JDK工具包，然后打开下载好的文件安装最新的Java JDK工具包。
## 1.3 安装最新版本的Eclipse
&emsp;&emsp;在[Eclipse 下载页](https://www.eclipse.org/downloads/packages/) 选择并下载最新的**Eclipse IDE for Java Developers** 版本 (推荐)。 
  
&emsp;&emsp;解压下载好的压缩文件并保存解压得到的文件夹。你不需要安装任何东西。或者，你也可以尝试Eclipse安装程序。
## 1.4 Windows下安装OpenCV 3.x
&emsp;&emsp;首先从[这里](https://opencv.org/releases/)下载OpenCV库（3.x版本）。  
 
&emsp;&emsp;然后解压已下载的OpenCV文件到你选择的位置并保存解压后的**opencv**文件夹。  
  
&emsp;&emsp;接下来你只需要两份文件：位于\opencv\build\java的opencv-3xx.jar文件、位于\opencv\build\java\x64的opencv_java3xx.dll库（64位系统）或位于\opencv\build\java\x8的opencv_java3xx.dll库（32位系统）。每份文件名称中的*3xx*后缀都是关于当前OpenCV版本的快捷方式。例如，对于OpenCV 3.0后缀为*300*；对于OpenCV 3.3后缀为*330*。
## 1.5 macOS下安装OpenCV 3.x
&emsp;&emsp;macOS下安装OpenCV最快的方法是使用[Homebrew](https://brew.sh/)。Homebrew安装完毕之后，必须检查你的系统是否已经安装了*XCode命令行工具*。
  
&emsp;&emsp;为此，打开终端并执行**xcode-select --install**。如果macOS要求安装此类工具，则下载并安装*XCode命令行工具*。否则继续安装OpenCV。
      
&emsp;&emsp;请确认安装OpenCV必备的Apache Ant已经安装完毕。否则，请通过Homebrew: **brew install ant**安装。同时，Apache Ant应当保存在 **/usr/local/bin/ant**这个位置。  

&emsp;&emsp;为了使用Homebrew安装Java版本的OpenCV，你需要在Homebrew中编辑opencv的公式来添加对Java版本的支持：**brew edit opencv**。打开文本编辑器，修改以下行：**-DBUILD_opencv_java=OFF in -DBUILD_opencv_java=ON**。保存文件后，即可安装OpenCV：**brew install --build-from-source opencv**。  

&emsp;&emsp;OpenCV完成安装后，所需的jar文件和dylib库将位于 **/usr/local/Cellar/opencv/3.x.x/share/OpenCV/java/** （比如/usr/local/Cellar/opencv/3.3.1/share/OpenCV/java/）。

&emsp;&emsp;请注意：如果你是将OpenCV从较早版本更新到最新版本的，此方法无效！你需要卸载原有的OpenCV并重新安装。
## 1.6 Linux下安装OpenCV 3.x
&emsp;&emsp;请注意：以下教程同样适用于Windows或macOS下编译OpenCV。Linux软件包管理系统（_apt-get_、*yum*等）可以提供OpenCV库的所需版本。

&emsp;&emsp;首先，下载并安装[CMake](https://cmake.org/download/)和[Apache Ant](http://ant.apache.org/)。然后下载OpenCV库，下载地址为[OpenCV库网站](https://opencv.org/releases/)。接着解压缩已下载的OpenCV文件到选好的位置，并打开CMake（cmake-gui）。在 **“Where is the source code field”** 输入解压出来的OpenCV库所在位置（例如/opencv/）；在 **“Where to build the binaries field”** 插入构件的目的目录（例如/opencv/build)。最后，选中复选框“Grouped”、“Advanced”。  
  
 ![UC6u2d.png](https://images.gitee.com/uploads/images/2020/0708/234339_338fa77f_1464254.png)  
     
&emsp;&emsp;现在按下 **“Configure”** 并使用**Unix Makefiles**的默认编译器。务必确认已经安装C/C++编译器。  
  
&emsp;&emsp;在 **“Ungrouped Entries”** 组，插入路径到Apache Ant可执行文件（比如**/apache-ant-1.9.6/bin/ant**）。  
  
&emsp;&emsp;在 **“BUILD”** 组，取消选择：   
 
&emsp;&emsp;&emsp;&emsp;• **BUILD_PERF_TESTS**  

&emsp;&emsp;&emsp;&emsp;• **BUILD_SHARED_LIBRARY**，使动态库完全绑定于Java
 
&emsp;&emsp;&emsp;&emsp;• **BUILD_TESTS**  

&emsp;&emsp;&emsp;&emsp;• **BUILD_opencv_python**  
  
 &emsp;&emsp;在“**CMAKE**”组，开始“Debug”（或“Release”）**“CMAKE_BUILD_TYPE”**。
 
 &emsp;&emsp;在**Java**组：  

&emsp;&emsp;&emsp;&emsp; • 插入Java AWT包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/** ）；

&emsp;&emsp;&emsp;&emsp; • 插入Java AWT库路径（例如 **/usr/lib/jvm/java-1.8.0/include/jawt.h** ）； 
  
&emsp;&emsp;&emsp;&emsp; • 插入Java包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/** ）；  
   
&emsp;&emsp;&emsp;&emsp; • 插入备用Java包含路径（例如 **/usr/lib/jvm/java-1.8.0/include/linux** ）；
   
&emsp;&emsp;&emsp;&emsp; • 插入JYM库路径（例如 **/usr/lib/jvm/java-1.8.0/include/jni.h** ）。
   
&emsp;&emsp;连按两次 **“Configure”** ，CMake窗口应显示为白色背景。否则的话，请修复红线，并再按一次 **“Configure”** 。接下来，请按 **“Generate”** 并关闭CMake。  
 
 ![UCcFzj.png](https://images.gitee.com/uploads/images/2020/0708/234339_2eef6b3c_1464254.png)  
  
 &emsp;&emsp;现在打开终端，转到OpenCV的**build**文件夹，并使用**make-j**命令编译所有内容。**make-j**命令中，*-j*标记是用来指示*make*运行允许工作的最大线程数的，理论上加快了构件速度。   
 &emsp;&emsp;等待过程完成…  
 &emsp;&emsp;若一切运行顺利，在目录/opencv/build/bin中你将得到opencv-3xx.jar、在目录/opencv/build/lib中你将得到libopencv_java3xx.so。同样地，每份文件名称中的*3xx*后缀都是关于当前OpenCV版本的快捷方式。例如，对于OpenCV 3.0后缀为*300*；对于OpenCV 3.3后缀为*330*。  
 &emsp;&emsp;以上就是你安装时所需要的一切。
## 1.7 Eclipse中安装Java版本的OpenCV
&emsp;&emsp;打开Eclipse，选择一个用户空间。创建用户库，该库应可以支持接下来要创建的所有新项目。转到：**Window > Preferences....**。  
 
 ![UCgx58.png](https://images.gitee.com/uploads/images/2020/0708/234336_15a27f96_1464254.png)  
    
&emsp;&emsp;从菜单导航到**Java > Build Path > User Libraries**下，选择**New....**。键入库名（例如opencv），然后选择刚刚创建的用户库。点击**Add External JARs...**，从电脑中浏览并选择**opencv-3xx.jar**。添加完毕后，扩展jar文件，选择**Native library location**并点击**Edit....**。 
  
 ![UC2Cvj.png](https://images.gitee.com/uploads/images/2020/0708/234337_794d1e99_1464254.png)  
  
&emsp;&emsp;选择**External Folder...**，从电脑中浏览并选择包含OpenCV库的文件夹（例如Windows下的**C:\opencv\build\java\x64**）。  
   
  &emsp;&emsp;MacOS下，如果你**不是通过**Homebrew安装OpenCV的，则需要为.so文件创建一个软连接，连接扩展名为.dylib。举个例子，可以从终端输入**ln -s libopencv_java300.so libopencv_java300.dylib**。 
 
## 1.8 其他版本（实验版本）IDE中安装Java版本的OpenCV 
&emsp;&emsp;如果你正在使用的是IntelliJ，则可以通过VM参数-Djava.library.path=/opencv/build/lib指定库的位置。