# 第三章 第一个OpenCV的JavaFX应用程序

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请在[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html)查看。您还可以在
[https://github.com/opencv-java/](https://github.com/opencv-java/)找到源代码和资源。
---  
## 3.1 A JavaFX application with OpenCV
This tutorial will guide you through the creation of a simple JavaFX GUI application using the OpenCV library in Eclipse.  

## 3.2 What we will do in this tutorial
In this guide, we will:  
&emsp;&emsp;• Install the **e(fx)clipse** plugin and (optionally) _Scene Builder_.  
&emsp;&emsp;• Work with **Scene Builder**.  
&emsp;&emsp;• Write and Run our application.  

## 3.3 Your First Application in JavaFX
The application you will write by following this tutorial is going to capture a video stream from a webcam and, then,it will display it on the user interface (GUI). We will create the GUI with Scene Builder: it is will have a button, which will allow us to start and stop the stream, and a simple image view container where we will put each stream frame.
## 3.4 Installing e(fx)clipse plugin and Scene Builder
In Eclipse, install the **e(fx)clipse** plugin, by following the guide at http://www.eclipse.org/efxclipse/install.
html#fortheambitious. If you choose not to install such a plugin, you have to create a traditional **Java project**, only. Download and install _JavaFX Scene Builder 2.0_ from [http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html](http://www.oracle.com/technetwork/java/
javafxscenebuilder-1x-archive-2199384.html).  
Now you can create a new JavaFX project. Go to **File > New > Project...** and select **JavaFX
project....**