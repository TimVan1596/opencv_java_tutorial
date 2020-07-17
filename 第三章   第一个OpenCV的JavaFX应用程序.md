# 第三章 第一个OpenCV的JavaFX应用程序

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请在[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html)查看。您还可以在
[https://github.com/opencv-java/](https://github.com/opencv-java/)找到源代码和资源。
---  
## 3.1 OpenCV的JavaFX应用程序
&emsp;&emsp;本教程将指导你使用Eclipse中的OpenCV库来创建一个简单的JavaFX GUI应用程序。

## 3.2 在本教程中要做什么
&emsp;&emsp;在本教程中，我们将：  

&emsp;&emsp;&emsp;&emsp;•安装**e(fx)clipse**插件和 _Scene Builder_ （*Scene Builder*安装不做硬性要求）；  

&emsp;&emsp;&emsp;&emsp;•使用 _Scene Builder_ ; 

&emsp;&emsp;&emsp;&emsp;•编写并运行应用程序。 

## 3.3 JavaFX中的第一个应用程序
&emsp;&emsp;本教程编写出来的应用程序将捕获来自网络摄像机的视频流并将其显示在图形用户界面（GUI）上。  
  
&emsp;&emsp;我们是使用Scene Builder来创建GUI的。创建完毕后，GUI将具有一个按钮和一个简单的图像视图框，前者用于播放/关闭视频流，后者用于放置视频流帧。
## 3.4 安装e(fx)clipse插件和Scene Builder
&emsp;&emsp;请按照本教程的指导在Eclipse中安装**e(fx)clipse**插件，本教程内容详见[http://www.eclipse.org/efxclipse/install.html#fortheambitious](http://www.eclipse.org/efxclipse/install.html#fortheambitious)。  
  
&emsp;&emsp;如果不想安装此类插件，只需创建一个惯用的**Java项目**——*JavaFX Scene Builder 2.0*即可。请从[http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html](http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html)下载安装*JavaFX Scene Builder 2.0*。
  
&emsp;&emsp;现在可以来新建一个JavaFX项目了，具体操作为：  
  
&emsp;&emsp;&emsp;&emsp;•转到“File > New > Project...”，选择“JavaFX project....”；  
 
![U8Puid.png](https://images.gitee.com/uploads/images/2020/0716/170447_07d86fe4_1464254.png)  
  
&emsp;&emsp;&emsp;&emsp;•输入项目名称（名称自选），单击“Next”；  
  
![U8P7wD.png](https://images.gitee.com/uploads/images/2020/0716/170455_2965d862_1464254.png)  
  
&emsp;&emsp;&emsp;&emsp;•添加OpenCV用户库到刚刚创建的项目，单击“Next”；  
  
![U8iv4J.png](https://images.gitee.com/uploads/images/2020/0716/170447_73b87349_1464254.png)  
  
&emsp;&emsp;&emsp;&emsp;•分别选定Package名称、*FXML文件*名称以及*控制器类*名称。关于你创建的GUI的描述将以FXML语言的形式包含在FXML文件中。而GUI组件与用户交互时所必须调用、管理的方法和事件都将由*控制器类*处理。
  
## 3.5 使用Scene Builder
&emsp;&emsp;如果之前已经安装过*Scene Builder*，就可以直接在Eclipse中右键单击FXML文件然后选择“Open with SceneBuilder”。  
 
&emsp;&emsp; _Scene Builder_ 是通过与图形界面交互来帮助构建你的GUI的。这样一来，你就可以实时预览你的窗口效果。此外，只需编辑图形预览即可实现GUI组件内容的修改以及位置的调整。  
  
&emsp;&emsp;不妨来具体地看一看我到底在讲些什么。
   
&emsp;&emsp;*FXML文件*最开始只有一个*AnchorPane*。AnchorPane中，允许存在一个偏离距离，位于AnchorPane子节点边缘锚定的位置与AnchorPane自身边缘所在的位置之间。如果AnchorPane设置了border和（或）padding，则偏离距离要从它们的内边缘开始算起。对于受到AnchorPane管理的子节点，无论它们是否可见，都将被AnchorPane一一展开。而非托管子节点则不会被AnchorPane展开。  
  
&emsp;&emsp;当然，你也可以删除AnchorPane并添加BorderPane。BorderPane在TOP、LEFT、RIGHT、BOTTOM以及CENTER这5个固定位置展开子节点。  

![U8k6w8.png](https://images.gitee.com/uploads/images/2020/0716/170450_ecd69550_1464254.png)  
   
 &emsp;&emsp;从“Container”菜单中拖拽一个BorderPane并将其放到“Hierarchy”菜单中，即可添加一个BorderPane。BorderPane添加完毕后，我们再来添加一个Button,它之后可以用来播放/关闭视频流。从“Contols”菜单中拖拽一个Button并将其放到我们刚刚添加的BP（即BorderPane）的**BOTTOM**区域，Button就添加完成了。  
  
 &emsp;&emsp;我们现在可以看到，界面的右方区域有3个菜单（“Properties”、“Layout”、“Code”），用于自定义被选中组件。例如，我们可以在“Properties”菜单下的“Text”区域修改之前添加的Button内容为“StartCamera”，还可以在“Code”菜单下的“fx:id”区域修改Button的id(比如改成“start_btn”)。接下来在从**控制器**方法编辑button属性时，我们就需要用到button的id。  

&emsp;&emsp;在界面中还可以看到，button现在离窗口的距离特别近。因此要为button设置一定的下边距。我们可以在“Layout”菜单中进行相应操作。  

![U8kzOx.png](https://images.gitee.com/uploads/images/2020/0716/170449_80184d49_1464254.png)  
  
![U8AEpd.png](https://images.gitee.com/uploads/images/2020/0716/170448_d93bfe99_1464254.png)  
 
&emsp;&emsp;为了能让button正常运行，我们必须在“Code”菜单下的“OnAction”这一栏设定好方法名称（比如“startCamera”），此处设定的方法将执行我们预想的功能。  

![U8EPuq.png](https://images.gitee.com/uploads/images/2020/0716/170449_b1f17c57_1464254.png)  
  
&emsp;&emsp;然后从“Controls”菜单中拖拽一个*ImageView*添加到BP的**CENTER**区域中。同样地，为ImageView设置一定的边距并对其id加以修改（比如改成“currentFrame”）。  

![U8EzdK.png](https://images.gitee.com/uploads/images/2020/0716/170450_2dc463fe_1464254.png)  
  
&emsp;&emsp;最后，必须指定一个控制器类去管理我们的GUI。为此，需添加我们之前选定的控制器类名称到位于窗口左下方的“Controller”菜单下的“Controller class”这一栏。 

&emsp;&emsp;我们刚刚使用Scene Builder创建了我们第一个GUI。如果你现在保存文件回到Eclipse，你会看到Eclipse已经自动生成了某些FXML代码。 
## 3.6 JavaFX中的一些重要概念
&emsp;&emsp;**Stage**：应用程序显示的地方（比如Windows窗口）；  
  
&emsp;&emsp;**Scene**：即节点容器，此容器中的节点构成了你的应用程序的某个“页面”；  
  
&emsp;&emsp;**Node**：Scene中的一个元素，具有可视化、可交互的特点。节点可能是以分层嵌套的形式存在于Scene中。  
  
&emsp;&emsp;在*Main类*中，我们需要将自身的*primary stage*传递给*start*函数： 
```
public void start(Stage primaryStage)
```
&emsp;&emsp;也是在*Main类*中，我们还要载入FXML文件，该文件将会填充我们的Stage、Scene的*root element*以及控制器类： 
  
```
FXMLLoader loader = new FXMLLoader(getClass().getResource("FXHelloCV.fxml"));
BorderPane root = (BorderPane) loader.load();
FXController controller = loader.getController();   
```  

## 3.7 使用控制器类管理GUI交互
&emsp;&emsp;关于我们的JavaFX应用程序，我们需要做两件最基本的事：一是控制按下Button；二是控制刷新ImageView。为了实现上述操作，我们需要在GUI组件和控制器类变量间创建一个引用：  
 
```
@FXML
private Button button;
@FXML
private ImageView currentFrame;  
```  
&emsp;&emsp;**@FXML**标签用于链接变量到FXML文件中的某个元素，并且该变量值应等于相链接的元素的id。  

&emsp;&emsp;**@FXML**标签用于某个元素设定的方法时，功能同上。例如：  

&emsp;&emsp;&emsp;&emsp;对于：  
```
<Button fx:id="button" mnemonicParsing="false" onAction="#startCamera" text="Start
˓→ Camera" BorderPane.alignment="CENTER">  
```  

&emsp;&emsp;&emsp;&emsp;我们设置：  
```
@FXML
protected void startCamera(ActionEvent event) { ...  
```  

## 3.8 视频捕获
&emsp;&emsp;VideoCapture类基本上已经整合了视频处理所需要的一切函数。这是建立在FFmpeg开源库的基础上的。
```
private VideoCapture capture = new VideoCapture();  
```  
&emsp;&emsp;一段视频由若干连续的图像组成，其中的这些图像我们称之为帧。视频文件中，用帧率来明确两帧之间的间隔时长。而对于摄像机来说，每秒可数字化的帧数通常是有限制的。在这里，我们设置帧率为30帧/秒。为此我们需要初始化一个计时器（即`ScheduledExecutorService`），该计时器每33毫秒将会启动一次后台任务。 
```
Runnable frameGrabber = new Runnable() { ... }
this.timer = Executors.newSingleThreadScheduledExecutor();
             this.timer.scheduleAtFixedRate(frameGrabber, 0, 33, TimeUnit.
˓→ MILLISECONDS);  
```  

&emsp;&emsp;要检查VideoCapture类是否成功绑定了视频源的话，我们需要使用**isOpened**函数：
  
```
if (this.capture.isOpened()) { ... }  
```  
&emsp;&emsp;视频在其析构函数被调用时就会自动关闭。可是如果你想在此之前就关闭视频的话，就需要调用其释放函数了：
  
```
this.capture.release();  
```  

&emsp;&emsp;鉴于视频帧纯粹就是图像而已，所以我们只需要将它们从VideoCapture对象中提取出来再放入Mat 1即可。  
  
```
Mat frame = new Mat();  
```  

&emsp;&emsp;从“read”或“overloaded >> operator”读取帧时，由于视频流都是连续的，所以帧可能是顺次而出。  
  
```
this.capture.read(frame);  
```  

&emsp;&emsp;我们还需要将我们的图像从*BGR*格式转换成*灰度*图。OpenCV中有一个非常好的函数可以完成此类转换：
  
```
Imgproc.cvtColor(frame, frame, Imgproc.COLOR_BGR2GRAY);  
```  

&emsp;&emsp;**从上面这行代码可以看到，cvtColor用到以下参数：**  
  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;•**源图像（frame）；** 
         
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;•**目标图像（frame），用来保存转换后的灰度图；**  

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;•**附加参数，用于指示将要执行何种转换。在这里使用的附加参数是COLOR_BGR2GRAY （不使用imread是因为对于彩色图像imread默认使用BGR通道顺序）。**
 
&emsp;&emsp;为了能将捕获的帧放入ImageView中，我们需要将矩阵转换成图像。具体操作如下：  
&emsp;&emsp;&emsp;&emsp;•首先，我们创建一个缓冲区，用于存储矩阵。  
```
MatOfByte buffer = new MatOfByte();  
```  

&emsp;&emsp;&emsp;&emsp;•然后，使用**imencode**函数，将捕获的帧放入缓冲区，下列这行代码便会将图像编码到内存缓冲区中： 
```
Imgcodecs.imencode(".png", frame, buffer);  
```  

&emsp;&emsp;&emsp;&emsp;**imencode**函数压缩图像并存储到内存缓冲区中，内存缓冲区会自适应压缩后图像的大小。

---
**注意：** **imencode**函数返回**CV_8UC1**型的单行矩阵，被编码成字节数组的图像就包含在返回的矩阵中。

---  

&emsp;&emsp;&emsp;&emsp;**imencode函数用到3个参数：**  
 
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;•**“.png”，即文件扩展名，用于定义输出格式；**

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**•frame，即待写入图像；**  

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**•buffer，即输出缓存区，可以自适应压缩后图像的大小。**  
 
&emsp;&emsp;将捕获的帧放入缓存区后，我们就要用到**ByteArrayInputStream**来流式传输缓存区中被压缩的图像：  
```
new Image(new ByteArrayInputStream(buffer.toArray()));  
```  

&emsp;&emsp;通过流式传输得到新的图像后，我们就可以将其放到ImageView中。不过使用Java 1.8版本时，我们是无法在与主线程不同的线程中更新GUI的元素的。因此我们需要先从其他的线程中获取新帧，然后在主线程中刷新我们的ImageView：
```
Image imageToShow = grabFrame();
Platform.runLater(new Runnable() {
        @Override public void run() { currentFrame.setImage(imageToShow); }
});  
```  
![U8u2zF.png](https://images.gitee.com/uploads/images/2020/0716/170452_e1829e8e_1464254.png)
  