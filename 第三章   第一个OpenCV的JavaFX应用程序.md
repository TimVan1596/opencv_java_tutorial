# 第三章 第一个OpenCV的JavaFX应用程序

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请在[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html)查看。您还可以在
[https://github.com/opencv-java/](https://github.com/opencv-java/)找到源代码和资源。
---  
## 3.1 A JavaFX application with OpenCV
## 3.1 OpenCV的JavaFX应用程序
This tutorial will guide you through the creation of a simple JavaFX GUI application using the OpenCV library in Eclipse.  
&emsp;&emsp;本教程将指导你使用Eclipse中的OpenCV库来创建一个简单的JavaFX GUI应用程序。

## 3.2 What we will do in this tutorial
## 3.2 在本教程中要做什么
In this guide, we will:  
在本教程中，我们将：  

&emsp;&emsp;• Install the **e(fx)clipse** plugin and (optionally) _Scene Builder_.  
&emsp;&emsp;•安装**e(fx)clipse**插件*和Scene Builder*（Scene Builder安装不做硬性要求）；  

&emsp;&emsp;• Work with **Scene Builder**.  
&emsp;&emsp;•使用Scene Builder;

&emsp;&emsp;• Write and Run our application.  
&emsp;&emsp;•编写并运行应用程序 

## 3.3 Your First Application in JavaFX
## 3.3 JavaFX中的第一个应用程序
The application you will write by following this tutorial is going to capture a video stream from a webcam and, then,it will display it on the user interface (GUI). We will create the GUI with Scene Builder: it is will have a button, which will allow us to start and stop the stream, and a simple image view container where we will put each stream frame.  
&emsp;&emsp;按照本教程编写出来的应用程序将捕获来自网络摄像机的视频流并将其显示在图形用户界面（GUI）上。我们是使用Scene Builder来创建GUI的。创建完毕后，GUI将具有一个按钮和一个简单的图像视图框，前者用于播放/关闭视频流，后者用于放置视频流帧。
## 3.4 Installing e(fx)clipse plugin and Scene Builder
## 3.4 安装e(fx)clipse插件和Scene Builder
In Eclipse, install the **e(fx)clipse** plugin, by following the guide at [http://www.eclipse.org/efxclipse/install.html#fortheambitious](http://www.eclipse.org/efxclipse/install.html#fortheambitious). If you choose not to install such a plugin, you have to create a traditional **Java project**, only. Download and install _JavaFX Scene Builder 2.0_ from[http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html](http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html).  
&emsp;&emsp;请按照本教程的指导在Eclipse中安装**e(fx)clipse**插件，详见[http://www.eclipse.org/efxclipse/install.html#fortheambitious](http://www.eclipse.org/efxclipse/install.html#fortheambitious)。如果不想安装此类插件，只需创建一个惯用的**Java项目**——*JavaFX Scene Builder 2.0*即可。请从[http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html](http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html)下载安装*JavaFX Scene Builder 2.0*。
  
Now you can create a new JavaFX project. Go to **File > New > Project...** and select **JavaFX
project....**  
&emsp;&emsp;接下来新建一个JavaFX项目，具体操作为：  
&emsp;&emsp;&emsp;&emsp;•转到“File > New > Project...”，选择“JavaFX project....”； 
![U8Puid.png](https://s1.ax1x.com/2020/07/12/U8Puid.png)  
  
Choose a name for your project and click _Next_.  
&emsp;&emsp;&emsp;&emsp;•输入项目名（名称任选），单击“Next”；  
  
![U8P7wD.png](https://s1.ax1x.com/2020/07/12/U8P7wD.png)  
  
Now add your OpenCV user library to your project and click _Next_.  
&emsp;&emsp;&emsp;&emsp;•添加OpenCV用户库到刚刚创建的项目，单击“Next”；  
  
![U8iv4J.png](https://s1.ax1x.com/2020/07/12/U8iv4J.png)  
  
Choose a name for your package, for the _FXML file_ and for the _Controller Class_. The _FXML file_ will contain the description of your GUI in FXML language, while the _Controller Class_ will handle all the method and event which
have to be called and managed when the user interacts with the GUI’s components.  
&emsp;&emsp;&emsp;&emsp;•分别选定Package名称、*FXML文件*名称以及*控制器类*名称。关于你创建的GUI的描述将以FXML语言的形式包含在FXML文件中。而GUI组件与用户交互时所必须调用、管理的方法和事件都将由控制器类处理。
  
## 3.5 Working with Scene Builder
## 3.5 使用Scene Builder
If you have installed _Scene Builder_ you can now right click on your _FXML file_ in Eclipse and select **Open with SceneBuilder**.  
&emsp;&emsp;如果之前已经安装过*Scene Builder*，就可以直接在Eclipse中右键单击FXML文件并选择“Open with SceneBuilder”。  
 
 _Scene Builder_ can help construct you gui by interacting with a graphic interface; this allows you to see a real time preview of your window and modify your components and their position just by editing the graphic preview.  
 &emsp;&emsp;Scene Builder是通过与图形界面交互来帮助构建你的GUI的。这样一来，你就可以实时预览你的窗口效果。此外，只需编辑“图形预览”即可实现GUI组件内容的修改以及位置的调整。  
  
   Let’s take a look at what I’m talking about.  
 &emsp;&emsp;让我们来看一下具体怎么做。
   
   At fist the _FXML file_ will have just an _AnchorPane_. An AnchorPane allows the edges of child nodes to be anchored to an offset from the anchorpane’s edges. If the anchorpane
has a border and/or padding set, the offsets will be measured from the inside edge of those insets. The anchorpane lays out each managed child regardless of the child’s visible property value; unmanaged children are ignored for all layout calculations. You can go ahead and delete the anchorpane and add a _BorderPane_ instead. A BorderPane lays out children in top, left, right, bottom, and center positions.  
  &emsp;&emsp;*FXML文件*最开始只有一个*AnchorPane*。AnchorPane允许其子节点边缘锚定的位置偏离自身边缘所在的位置。如果AnchorPane设置了边框和（或）填充，则偏离距离是从填充物的内部边缘开始测算的。对于受到管理的子节点，无论它们是否可见，都将被AnchorPane一一展开。而非托管子节点则不会被AnchorPane展开。当然，你也可以删除AnchorPane并添加BorderPane。BorderPane在TOP、LEFT、RIGHT、BOTTOM以及CENTER这5个固定位置展开子节点。
![U8k6w8.png](https://s1.ax1x.com/2020/07/12/U8k6w8.png)  
  
You can add a BorderPane by dragging from the **Container** menu a borderpane and then drop it in the **Hierarchy** menu. Now we can add the button that will allow us to start and stop the stream. Take a button component from the
**Controls** menu and drop it on the **BOTTOM** field of our BP. As we can see, on the right we will get three menus(Properties, Layout, Code) which are used to customize our selected component. For example we can change text of
our button in“StartCamera”in the **Text** field under the **Properties** menu and the id of the button(e.g. “start_btn”) in the **fx:id** field under the **Code** menu.  
 &emsp;&emsp;从**Container**菜单中拽一个BorderPane并将其放到**Hierarchy**菜单中，即可添加一个BorderPane。BorderPane添加完毕后，我们再来添加一个Button,它之后可以用来播放/关闭视频流。从**Contols**菜单中拽一个Button并将其放到我们刚刚添加的BP（即BorderPane）的**底部**区域。我们可以看到，下图中右边区域有3个菜单（Properties、Layout、Code），用于自定义被选中组件。例如，我们可以在**Properties**菜单下的**Text**区域修改之前添加的Button内容为“StartCamera”，还可以在**Code**菜单下的**fx:id**区域修改Button的id(比如改成“start_btn”)。
![U8kzOx.png](https://s1.ax1x.com/2020/07/12/U8kzOx.png)  
  
![U8AEpd.png](https://s1.ax1x.com/2020/07/12/U8AEpd.png)  
 
We are going to need the id of the button later, in order to edit the button properties from our **Controller**'s methods. As you can see our button is too close to the edge of the windows, so we should add some bottom margin to it; to do so we can add this information in the **Layout** menu. In order to make the button work, we have to set the name of the method (e.g. “startCamera”) that will execute the action we want to preform in the field **OnAction** under the **Code** menu.  
接下来在从**控制器**方法编辑button属性时，我们将需要用到button的id。  
可以看到，button现在离窗口的距离特别近，因此要为button设置一定的下边距。我们可以在**Layout**菜单中进行相应操作。  
为了能让button正常运行，我们必须在**Code**菜单下的**OnAction**这一栏设定好方法名称（比如“startCamera”），此处设定的方法将执行我们预想的功能。
![U8EPuq.png](https://s1.ax1x.com/2020/07/12/U8EPuq.png)  
  
Now, we shall add an _ImageView_ component from the **Controls** menu into the **CENTER** field of our BP. Let’s also edit the id of the image view (e.g. “currentFrame”), and add some margin to it.  
 然后从**Controls**菜单中拽一个*ImageView*添加到BP的**CENTER**区域中。同样地，为ImageView设置一定的边距并对其id加以修改（比如改成“currentFrame”）。
![U8EzdK.png](https://s1.ax1x.com/2020/07/12/U8EzdK.png)  
  
Finally we have to tell which Controller class will manage the GUI, we can do so by adding our controller class name in the **Controller class** field under the **Controller** menu located in the bottom left corner of the window.    
最后，必须指定一个控制器类去管理我们的GUI。为此，需添加我们之前选定的控制器类名称到位于窗口左下方的**Controller**菜单下的**Controller class**这一栏。 

We just created our first GUI by using Scene Builder, if you save the file and return to Eclipse you will notice that some FXML code has been generated automatically.  
我们刚刚使用Scene Builder创建了我们第一个GUI。如果你现在保存文件回到Eclipse，你会看到Eclipse已经自动生成了某些FXML代码。 
## 3.6 Key Concepts in JavaFX
## 3.6 JavaFX中的一些重要概念
The **Stage** is where the application will be displayed (e.g., a Windows’ window). A **Scene** is one container of Nodes that compose one “page” of your application. A **Node** is an element in the Scene, with a visual appearance and an interactive behavior. Nodes may be hierarchically nested . In the _Main class_ we have to pass to the _start_ function our _primary stage_:  
**Stage**：应用程序显示的地方（比如Windows窗口）；  
**Scene**：即容器，之中包含组成应用程序的节点；  
**Node**：Scene中的一个元素，具有可视化、可交互的特点。节点可能是以分层嵌套的形式存在于Scene中。  
Main class中需要将我们的*primary stage*传递给start函数： 
```
public void start(Stage primaryStage)
```

and load the fxml file that will populate our stage, the _root element_ of the scene and the controller class: 
并且载入FXML文件。该文件将会填充我们的Stage、Scene的*root element*以及控制器类： 
  
```
FXMLLoader loader = new FXMLLoader(getClass().getResource("FXHelloCV.fxml"));
BorderPane root = (BorderPane) loader.load();
FXController controller = loader.getController();   
```  

## 3.7 Managing GUI Interactions With the Controller Class
## 3.7 控制器类管理GUI交互
For our application we need to do basically two thing: control the button push and the refreshment of the image view.
To do so we have to create a reference between the gui components and a variable used in our controller class:  
关于我们的JavaFX应用程序，我们需要做最基本的两件事：一是控制按下Button；二是控制刷新ImageView。为了实现上述操作，我们需要在GUI组件和控制器类变量间创建一个引用：  
 
```
@FXML
private Button button;
@FXML
private ImageView currentFrame;  
```  

The **@FXML** tag means that we are linking our variable to an element of the fxml file and the value used to declare the variable has to equal to the id set for that specific element.  
**@FXML**标签用于链接变量到FXML文件中的某个元素，并且该变量值应等于相链接的元素的id。  

The **@FXML** tag is used with the same meaning for the Actions set under the Code menu in a specific element.  
**@FXML**标签用于某个元素设定的方法时，功能同上。  

for:  
对于：  
```
<Button fx:id="button" mnemonicParsing="false" onAction="#startCamera" text="Start
˓→ Camera" BorderPane.alignment="CENTER">  
```  

we set:  
我们设置：  
```
@FXML
protected void startCamera(ActionEvent event) { ...  
```  

## 3.8 Video Capturing
## 3.8 视频捕获
Essentially, all the functionalities required for video manipulation is integrated in the VideoCapture class.  
VideoCapture类基本上已经整合了视频处理所需要的一切函数。  
```
private VideoCapture capture = new VideoCapture();  
```  

This on itself builds on the FFmpeg open source library. A video is composed of a succession of images, we refer to these in the literature as frames. In case of a video file there is a frame rate specifying just how long is between two frames. While for the video cameras usually there is a limit of just how many frames they can digitalize per second. In our case we set as frame rate 30 frames per sec. To do so we initialize a timer (i.e., a
`ScheduledExecutorService`) that will open a background task every 33 _milliseconds_.  
这是建立在FFmpeg开源库的基础上的。一段视频由若干连续的图像组成，其中这些图像我们称之为帧。视频文件中，用帧率来明确两帧之间的间隔时长。而对于摄像机来说，每秒可数字化的帧数是有限制的。在这里，我们设置帧率为30帧/秒。如何设置？我们需要初始化一个计时器，该计时器每33毫秒将会启动一次后台任务。 
```
Runnable frameGrabber = new Runnable() { ... }
this.timer = Executors.newSingleThreadScheduledExecutor();
             this.timer.scheduleAtFixedRate(frameGrabber, 0, 33, TimeUnit.
˓→ MILLISECONDS);  
```  

To check if the binding of the class to a video source was successful or not use the **isOpened** function:  
要检查VideoCapture类是否成功绑定了视频源的话，我们使用**isOpened**函数。
  
```
if (this.capture.isOpened()) { ... }  
```  

Closing the video is automatic when the object's destructor is called. However, if you want to close it before this you need to call its release function.   
调用对象的析构函数时，视频自动关闭。可是如果你想在调用前就关闭视频的话，就需要调用其释放函数了。 
  
```
this.capture.release();  
```  

The frames of the video are just simple images. Therefore, we just need to extract them from the VideoCapture object and put them inside a Mat one.
视频帧纯粹就是图像而已。因此，我们只需要将它们从VideoCapture对象中提取出来再放入Mat 1即可。  
  
```
Mat frame = new Mat();  
```  

The video streams are sequential. You may get the frames one after another by the read or the overloaded >> operator.
视频流是有顺序的。因此，从“read”或“overloaded >> operator”读取时，帧都是顺次而出。  
  
```
this.capture.read(frame);  
```  

Now we are going to convert our image from _BGR_ to _Grayscale_ format. OpenCV has a really nice function to do this kind of transformations:  
我们还需要将我们的图像从*BGR*格式转换成*灰度*图。OpenCV有一个非常nice的函数可以完成此类转换：
  
```
Imgproc.cvtColor(frame, frame, Imgproc.COLOR_BGR2GRAY);  
```  

**As you can see, cvtColor takes as arguments**:  
**可以看到，cvtColor是作为参数的：**  
&emsp;&emsp;• a source image (frame)  
&emsp;&emsp;• 源图像（帧） 
         
&emsp;&emsp;• a destination image (frame), in which we will save the converted image.  
&emsp;&emsp;•目标图像（帧），用来保存转换后的灰度图  

&emsp;&emsp;• an additional parameter that indicates what kind of transformation will be performed. In this case we use
**COLOR_BGR2GRAY** (because of imread has BGR default channel order in case of color images).  
 &emsp;&emsp;•附加参数，用于指示将要执行何种转换。在这里使用的额外参数是**COLOR_BGR2GRAY** （不使用imread，因为对于彩色图像imread默认使用BGR通道顺序）
 
Now in order to put the captured frame into the ImageView we need to convert the Mat in a Image. We first create a buffer to store the Mat.  
为了能在ImageView中放入捕获的帧，我们需要将矩阵转换成图像。具体操作如下：  
首先，我们创建一个缓冲区，用于存储矩阵。  
```
MatOfByte buffer = new MatOfByte();  
```  

Then we can put the frame into the buffer by using the **imencode** function:  
然后，使用**imencode**函数，将捕获的帧放入缓冲区： 
```
Imgcodecs.imencode(".png", frame, buffer);  
```  

This encodes an image into a memory buffer. The function compresses the image and stores it in the memory buffer that is resized to fit the result.  
这行代码会将图像编码到内存缓冲区中。       
**imencode**函数压缩图像并存储到内存缓冲区中，内存缓冲区会自适应压缩后图像的大小。
---
**Note**: **imencode** returns single-row matrix of type **CV_8UC1** that contains encoded image as array of bytes.  
**注意：** **imencode**函数返回**CV_8UC1**型的单行矩阵，该矩阵包含了被编码成字节数组的图像。

---  

**It takes three parameters:**  
**imencode函数用到3个参数：**  
 
&emsp;&emsp;• (".png") File extension that defines the output format.
&emsp;&emsp;•“.png”，即文件扩展名，用于定义输出格式

&emsp;&emsp;• (frame) Image to be written.  
&emsp;&emsp;•帧，即待写入图像  

&emsp;&emsp;• (buffer) Output buffer resized to fit the compressed image.   
&emsp;&emsp;•缓存区，即输出缓存区，可以自适应压缩后图像的大小  
 
Once we filled the buffer we have to stream it into an Image by using **ByteArrayInputStream**:  
将捕获的帧放入缓存区后，我们就要用到**ByteArrayInputStream**来流式传输缓存区中被压缩的图像。  
```
new Image(new ByteArrayInputStream(buffer.toArray()));  
```  

Now we can put the new image in the ImageView. With _Java 1.8_ we cannot perform an update of a GUI element in a thread that differs from the main thread; so we need to get the new frame in a second thread and refresh our ImageView
in the main thread:  
现在我们可以将新的图像放入ImageView。使用Java 1.8时，我们是无法在与主线程不同的线程中更新GUI的元素。因此我们需要从其他的线程中获取新帧，然后在主线程中刷新我们的ImageView。  
```
Image imageToShow = grabFrame();
Platform.runLater(new Runnable() {
        @Override public void run() { currentFrame.setImage(imageToShow); }
});  
```  
![U8u2zF.png](https://s1.ax1x.com/2020/07/12/U8u2zF.png)
