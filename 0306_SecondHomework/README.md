# 0306_Second Homework
	by guozongxun
##01_反编译apk，并截图
###1、本次练习使用的app为`挖财记账理财`，首先重命名`*.apk`为`*.zip`，然后解压缩`*.zip`，找到`classes.dex`文件；
###2、进入反编译工具`dex2jar-0.0.9.15`目录下，将`classes.dex`文件复制到该目录下；
###3、快捷键`WIN+R`打开命令行，切换到`dex2jar-0.0.9.15`目录下，反编译dex文件，依次输入命令：
> d:  
> cd D:\7thExercise\AndroidDecompile\dex2jar-0.0.9.15  
> d2j-dex2jar.bat classes.dex
 
命令行截图如下：  
![01_decompile](https://raw.githubusercontent.com/Test-Seven/guozongxun/master/0306_SecondHomework/picture/01_decompile.png)
###4、查看当前目录，可以看到多出一个`classes-dex2jar.jar`文件，使用`jd-gui`打开该jar包，即可看到反编译之后的资源文件，截图如下：  
![01_gd-gui](https://raw.githubusercontent.com/Test-Seven/guozongxun/master/0306_SecondHomework/picture/01_gd-gui.png)

##02_使用aapt命令查询权限
###1、使用aapt命令查看`com.wacai365`的权限，截图如下：  
![02_appt命令查看com.wacai365权限](https://raw.githubusercontent.com/Test-Seven/guozongxun/master/0306_SecondHomework/picture/02_appt%E5%91%BD%E4%BB%A4%E6%9F%A5%E7%9C%8Bcom.wacai365%E6%9D%83%E9%99%90.png)

##03_编写3种不同切入点的Android monkey的命令，并成功运行，同时说明切入点是什么  
###01_仅指定随机数seed=1，随机事件1000次，输出日志为第三级别
> adb -d shell monkey -s 1 -v -v -v 1000

###02_指定随机数seed=2、应用为挖财、随机事件10000次、输出日志为第三级别
> adb -d shell monkey -s 2 -p com.wacai365 -v -v -v 10000

###03_指定随机数seed=5、固定延迟500ms、点击事件占比25%、滑动事件占比10%、轨迹事件占比0%、基本导航事件占比0%、主要导航事件占比10%、系统按键事件占比5%、启动activity占比2%、其他事件占比16%、监视android系统本地代码crash事件、程序异常时继续随机事件操作、应用为挖财、随机事件240000次
> adb -d shell monkey -s 5 -p com.wacai365 --throttle 500 --pct-touch 25 --pct-motion 30 --pct-trackball 0 --pct-nav 0 --pct-majornav 10 --pct-syskeys 5 --pct-appswitch 2 --pct-anyevent 16 --monitor-native-crashes --ignore-crashes -v -v -v 240000

##04_请找出Android monkey中motion和touch对应的源码里的方法，并找出monkey工具实现点击的最基础发方法是什么  

##05_找到任意一个apk or ipa，然后去寻找里面的db，并打开，上传截图  
  
##06_（mac专享）github上去找monkey.js 去instruments运行，给出instruments运行的结果图  

##07_（mac专享）安装idevicestaller，获取iOS日志  
  
#本次课后作业过程中，遇到问题：  
###1、反编译网易邮箱大师app，有异常提示，截图如下：  

反编译过程中分别使用了`dex2jar-0.0.7、dex2jar-0.0.9.15、dex2jar-2.0`三种版本的dex2jar工具，均有异常提示出现。
Google之后，发现有说是因为app做了反编译限制，

###2、
