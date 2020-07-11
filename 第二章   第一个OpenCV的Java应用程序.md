# 第二章 第一个OpenCV的Java应用程序  

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请在[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html)查看。您还可以在
[https://github.com/opencv-java/](https://github.com/opencv-java/)找到源代码和资源。
---  
## 2.1 OpenCV的Java应用程序
&emsp;&emsp;本教程将指导你使用Eclipse中的OpenCV库来创建一个简单的Java控制台应用程序。  

## 2.2 在本教程中要做什么 
在本教程中，我们将：  

&emsp;&emsp;•新建一个Java项目；  
            
&emsp;&emsp;•为新建的Java项目添加一个用户库；  
            
&emsp;&emsp;•编写OpenCV代码；  
            
&emsp;&emsp;•构建并运行应用程序。
  
## 2.3 新建Java项目
&emsp;&emsp;打开Eclipse并新建一个Java项目，具体操作如下：  
&emsp;&emsp;&emsp;&emsp;•打开“File”菜单，转到“New”并点击“Java Project”。
  
![UeC2B6.png](https://images.gitee.com/uploads/images/2020/0709/003848_6ef99d13_1464254.png) 
  
&emsp;&emsp;&emsp;&emsp;•在弹出的“New Java Project”对话框中，输入新建Java项目名称并点击“Finish”。
## 2.4 添加用户库
 &emsp;&emsp;如果你是从第一章（Java版本OpenCV的安装）看过来的，那么在你的工作空间的用户库中已经设置好了OpenCV库；如果不是，请查看前面教程。  
&emsp;&emsp;现在请准备将用户库添加到你新建的Java项目中，具体操作如下：  
&emsp;&emsp;&emsp;&emsp;•首先找到Eclipse的“Package Explorer”，在这之下，右键单击“My FirstProject”，转到*Build Path --> Add Libraries....*。
  
![UeSEpn.png](https://images.gitee.com/uploads/images/2020/0709/003847_67aade7f_1464254.png)  

&emsp;&emsp;&emsp;&emsp;•然后选择“User Libraries”，点击“Next”，选中OpenCV库的复选框并点击“Finish”。 
  
![UeSr9A.png](https://images.gitee.com/uploads/images/2020/0709/003846_63db9134_1464254.png)  
  
## 2.5 创建简单的应用程序
&emsp;&emsp;右键单击项目文件夹为你的项目新增一个类，然后转到*New --> Class*，输入名称（此名称既是包名也是类名）。   
&emsp;&emsp;接下来编写第一个应用程序的代码。  
&emsp;&emsp;&emsp;&emsp;•首先，定义**main**方法：
```  
public class HelloCV {
         public static void main(String[] args){  
                 System.loadLibrary(Core.NATIVE_LIBRARY_NAME);
                 Mat mat = Mat.eye(3, 3,CvType.CV_8UC1);
                 System.out.println("mat = " + mat.dump());
         }
}  
```
&emsp;&emsp;&emsp;&emsp;•在此方法中，我们先要载入之前的OpenCV本地库。
```  
System.loadLibrary(Core.NATIVE_LIBRARY_NAME);  
```
&emsp;&emsp;&emsp;&emsp;•然后定义一个新的矩阵。  

---
  **注意**：类中的矩阵表示n维密集数值的单通道或多通道数列。它可以用于存储实值矢量、复值矢量、矩阵、灰度图、彩色图、体素模型、矢量场、点云、张量以及直方图等。详情请看[OpenCV页面](http://docs.opencv.org/3.0.0/dc/d84/group__core__basic.html)。  
  
---
 
```  
Mat mat = Mat.eye(3, 3, CvType.CV_8UC1);
```  

&emsp;&emsp;&emsp;&emsp;•*Mat.eye*代表一个单位矩阵，我们设其尺寸为3x3、元素类型为CV_8UC1。   
  
&emsp;&emsp;如果你就这样完成代码，如你所见你会得到错误输出，这是因为Eclipse无法解析某些变量。你可以将光标放在有错误标记的单词上，等待对话框弹出并单击**Import**。对所有变量一一处理之后，我们就已经为代码添上了下列行：
 
```
import org.opencv.core.Core;
import org.opencv.core.CvType;
import org.opencv.core.Mat;
```  

&emsp;&emsp;现在我们不妨试着单击“Run”按钮来构建运行应用程序。输出应如下：    
  
 ![UeCpm6.png](https://images.gitee.com/uploads/images/2020/0709/003846_0e5bf15b_1464254.png)  
   
 &emsp;&emsp;源代码均可在[GitHub](https://github.com/opencv-java/getting-started/tree/master/HelloCV)找到。