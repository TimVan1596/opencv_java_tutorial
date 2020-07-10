# 第二章 第一个OpenCV的Java应用程序  

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请在[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html)查看。您还可以在
[https://github.com/opencv-java/](https://github.com/opencv-java/)找到源代码和资源。
---  
## 2.1 A Java application with OpenCV 
## 2.1 OpenCV的Java应用程序
This tutorial will guide you through the creation of a simple Java console application using the OpenCV library in Eclipse.  
本教程将指导你使用Eclipse中的OpenCV库来创建一个简单的Java控制台应用程序。  

## 2.2 What we will do in this tutorial 
## 2.2 在本教程中要做什么 
In this guide, we will:  
在本教程中，我们将：  

&emsp;&emsp;• Create a new Java Project  
&emsp;&emsp;•新建一个Java项目；  
            
&emsp;&emsp;• Add a User Library to the project  
&emsp;&emsp;•为新创建的Java项目添加一个用户库；  
            
&emsp;&emsp;• Write some OpenCV code  
&emsp;&emsp;•编写OpenCV代码；  
            
&emsp;&emsp;• Build and Run the application  
&emsp;&emsp;•构建并运行应用程序。
  
## 2.3 Create a New Project
## 2.3 新建Java项目
Open Eclipse and create a new Java project; open the _File_ menu, go to _New_ and click on _Java Project_.   
打开Eclipse并创建一个新的Java项目，具体操作如下：  
打开“File”菜单，转到“New”并点击“Java Project”。
  
![UeC2B6.png](https://images.gitee.com/uploads/images/2020/0709/003848_6ef99d13_1464254.png) 
  
In the _New Java Project_ dialog write the name of your project and click on _Finish_.  
在弹出的“New Java Project”对话框中，输入新建Java项目名称并点击“Finish”。
## 2.4 Add a User Library
## 2.4 添加用户库
If you followed the previous tutorial (_Installing OpenCV for Java_), you should already have the OpenCV library set in your workspace’s user libraries; if not please check out the previous tutorial. Now you should be ready to add the library to your project. Inside Eclipse’s _Package Explorer_ just right-click on your project’s folder and go to _Build Path --> Add Libraries...._ 
如果你是从第一章（Java版本OpenCV的安装）看过来的，你应该已经在你的工作空间
  
![UeSEpn.png](https://images.gitee.com/uploads/images/2020/0709/003847_67aade7f_1464254.png)  

Select _User Libraries_ and click on _Next_, check the checkbox of the OpenCV library and click _Finish_.  
  
![UeSr9A.png](https://images.gitee.com/uploads/images/2020/0709/003846_63db9134_1464254.png)  
  
## 2.5 Create a simple application
Now add a new Class to your project by right-clicking on your project’s folder and go to _New --> Class_. Write a name of your choice for both the package and the class then click on _Finish_. Now we are ready to write the code of
our first application. Let’s start by defining the **main** method:  
```  
public class HelloCV {
         public static void main(String[] args){  
                 System.loadLibrary(Core.NATIVE_LIBRARY_NAME);
                 Mat mat = Mat.eye(3, 3,CvType.CV_8UC1);
                 System.out.println("mat = " + mat.dump());
         }
}  
```
First of all we need to load the OpenCV Native Library previously set on our project.  
```  
System.loadLibrary(Core.NATIVE_LIBRARY_NAME);  
```
Then we can define a new Mat.   

---
**Note**: The class **Mat** represents an n-dimensional dense numerical single-channel or multi-channel array. It can be used to store real or complex-valued vectors and matrices, grayscale or color images, voxel volumes, vector fields,point clouds, tensors, histograms. For more details check out the OpenCV [page](http://docs.opencv.org/3.0.0/dc/d84/group__core__basic.html).   

---
 
```  
Mat mat = Mat.eye(3, 3, CvType.CV_8UC1);
```  

The _Mat.eye_ represents a identity matrix, we set the dimensions of it (3x3) and the type of its elements.   
  
As you can notice, if you leave the code just like this, you will get some error; this is due to the fact that eclipse can’t resolve some variables. You can locate your mouse cursor on the words that seem to be errors and wait for a dialog to pop up and click on the voice **Import....** If you do that for all the variables we have added to the code the following
rows:  
```
import org.opencv.core.Core;
import org.opencv.core.CvType;
import org.opencv.core.Mat;
```  

 We can now try to build and run our application by clicking on the Run button. You should have the following output:  
  
 ![UeCpm6.png](https://images.gitee.com/uploads/images/2020/0709/003846_0e5bf15b_1464254.png)  
   
 The whole source code is available on [GitHub](https://github.com/opencv-java/getting-started/tree/master/HelloCV).