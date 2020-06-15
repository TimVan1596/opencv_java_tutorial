#CHAPTER 4 OpenCV Basics  
#第四章 OpenCV基础

---
***Note***: We assume that by now you have already read the previous tutorials. If not, please check previous tutorials at
[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html). You can also find the source code and resources at
[https://github.com/opencv-java/](https://github.com/opencv-java/)
---

---
***注意***：我们假设您现在已经阅读了之前的教程。如果没有，请查看以前的教程，网址为
[http://opencv-java-tutorials.readthedocs.org/en/latest/index.html](http://opencv-java-tutorials.readthedocs.org/en/latest/index.html) 。您还可以在以下位置找到源代码和资源
[https://github.com/opencv-java/](https://github.com/opencv-java/)
---

##4.3 Color channel checkbox
The graphic interface is complete for the first task, now we need to work on the controller; in the previous tutorial we
could control the number of channels displayed on screen with the line:  
这个图形界面的第一个任务已经完成，现在我们需要在控制器上工作；在上一个教程中，我们
可以控制该行在屏幕上显示的频道数：
`
Imgproc.cvtColor(frame, frame, Imgproc.COLOR_BGR2GRAY);
`  
In order to control this conversion with the check box, we have to link the check box with a FXML variable:  
`@FXML
private CheckBox grayscale;`  
Now we can implement the control by adding a simple “if” condition which will perform the conversion only if our
check box is checked:  
`if (grayscale.isSelected())
{
Imgproc.cvtColor(frame, frame, Imgproc.COLOR_BGR2GRAY);
}`  
