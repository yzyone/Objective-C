
# windows下objective-c环境搭建 #

申明：本文为转自http://blog.csdn.net/ldl22847/article/details/7482971 及 http://www.cnblogs.com/xiangshancuizhu/p/3385008.html ，本人将两处搬移到一处

Objective-C是苹果软件的编程语言，想要上机学习、调试，有一个集成开发环境（IDE）方便很多。有三类方法搭建Objective-C的集成开发环境：

1)   使用苹果的平台，集成开发环境使用Xcode。但如果没有苹果平台，想在Windows环境下学习Objective-C，可以采用以下两种方法：

2)   在Windows环境下设置一个苹果虚拟机，但这对个人电脑的性能要求较高，不是所有个人电脑都可以，而且虚拟机的运行速度也较慢；

3)   采用Codeblocks IDE开发环境，对其进行配置，搭建成支持Object-C的编译、调试、运行的集成开发环境。这种方法对个人电脑的性能几乎没有要求，可以快速构建，本文介绍的是这一种方法。

 

## 1、安装Object-C的编译器 ##

Objective-C的编译器有很多，本文介绍使用GnuStep，网址是http://www.gnustep.org/experience/Windows.html，从这里可以下载Windows版本的gcc编译器：

    GNUstep MSYS System
    GNUstep Core
    GNUstep Devel

进入下载页面，下载上面3个软件包，进行安装，例如安装到D:\GNUstep。关于这3个软件包的作用，可以在网上查询，不再赘述。

 

## 2、安装Object-C的集成开发环境 ##

我们选择用CodeBlocks IDE作为Objective-C的集成开发环境，下载地址是：http://www.codeblocks.org/。

 

## 3、开发环境配置 ##

通过对Code blocks的配置，一步步完成Objective-C开发环境的搭建。CodeBlocks，可以看见这样的画面：

 

## 第一步：配置编译器 ##

进入Settings->Compiler anddebugger...，选择GNU GCC Compiler编译器，按“Copy”按钮，并重新命名为“GNUstep MinGW Compiler“并保存。如图：

 

之后进入Other Options 分页，录入：

-fconstant-string-class=NSConstantString -std=c99 如图：

 

 

## 第二步：连接器设置 Linkerstettings ##

在连接库（Link Libraries）中添加两个文件，如图。

它们在D:\GNUstep\GNUstep\System\Library\Libraries下面：

    libgnustep-base.dll.a
    libobjc.dll.a


## 第三步：指定搜索目录Searchdirectories（需要预先安装好GNUstep） ##

 

1)  Compiler（编译器）设置为D:\GNUstep\GNUstep\System\Library\Headers；

 

 

2)  Linker（连接器）设置为D:\GNUstep\GNUstep\System\Library\Libraries；

 

 

 

## 第四步：添加Objective-C文件类型支持 ##

1)进入Settings->Environment...，选择Files extension handling 添加*.m。如图：

 

2)进入 Project->Projecttree->Edit file types & categories... ，在Sources, 下面添加*.m到文件类型列表中。如图：

 

3)进入Settings->Editor...，选择 Syntaxhighlighting，点击“Filemasks....”按钮，在弹出框尾部添加*.m 到文件类型。如图：

 

 

4)点击“Keywords...”按钮 (紧靠Filemasks...按钮) 添加下面Object-C的关键字到EditKeywords列表中。如图。

    @interface @implementation @end  @class @selector @protocol @public @protected @private id BOOL YES NO SEL nil  NULL self

 

 

## 4.   代码测试 ##

上述开发环境配置完成后，就可以开始代码测试了。

首先，新建一个工程，选择File->New->Project…,会出现一个工程类型窗口，选择Console Application，然后按照工程建立指引，建立一个mytest的工程，并将main.c的文件更名为main.m，录入以下代码：

```
#import <Foundation/Foundation.h>

int main (int argc, const char *argv[])

{

    NSAutoreleasePool *pool =[[NSAutoreleasePool alloc] init];

    NSLog(@"%@",@"hello world");

    [pool drain];

    return 0;

}
```

如图：

 

 

之后再开始编译运行：Buid –> Run… 如果出现以下窗口，恭喜你，你已经成功的搭建了Windows下的Objective-C的集成开发环境。




---

另外，在别处看到，记事本写完代码，使用gcc工具编译，可解决一时之需，有需要的也可看看。

以下为转载内容：




对于Iphone开发学习者而言，Object -c 是必修的语言。但是由于苹果的自我封闭的产业链发展模式（从芯片、机器、开发语言、终端产品、服务）的限制，要想开发针对苹果iPhone等产品的应用程序，就需要用Mac机器，在Xcode的IDE上使用Objective C语言开发。所以，要想廉价方式学习Objective C就必须要在Windows上能搭建一个Objective C开发环境。 

在Windows下搭建Objective C开发环境，需要到http://www.gnustep.org/experience/Windows.htmlGNUstep官方网站上下载，四个软件包：GNUstep MSYS System、GNUstep Core、GNUstep Devel、Cairo Backend。其中，前两个软件包是必须要安装的，第三个软件包是安装一些开发工具，比如：gcc、g++等，所以如果是学习Objective C的话，这个包也是必须要安装，第四个软件包是安装glib等库，这个包安装不安装根据具体情况而定。

安装好后在“开始”菜单中“所有程序”下可以找到“GNUstep”->“shell”，就会出console窗口，可以试试一些Linux命令（ls,cd,mkdir等）。 

现在我们可以编写一个简单的代码进行测试，看看我们的环境是否已经搭建好了 

代码： 

```
#import <Foundation/Foundation.h>    
    
 int main( int argc, const char *argv[] ) {    
    
 NSLog(@"hello world\n");    
    
 return 0;    
    
}  
```

在Windows环境下用记事本等编写上述代码，并且保存到D:/home下，取名为helloworld.m。在GNUstep的console窗口命令行下， 

```
1. cd d:\home 

2. gcc -o helloworld helloworld.m -I/GNUstep/System/Library/Headers -fconstant-string-class=NSConstantString -L/GNUstep/System/Library/Libraries -lobjc -lgnustep-base 
```

3. 此话在home文件夹下会自动生成helloworld.exe文件。在终端输入 

    helloworld.exe 

helloworld.exe编译并运行成功的话，说明windows下Objective C开发环境就搭建好了 

说明：第二步中的一些参数明说，如果熟悉Linux/Unix下C/C++编译的话，上述参数应该很熟悉，-I表示头文件查找的路径，-L表示库文件查找路径，-l表示需要链接的库文件。但是，-fconstant-string-class=NSConstantString  对于这个参数可能比较陌生，这个参数主要是指定常量字符串所使用的class。 

如果在终端显示找不到头文件，建议考虑把那些软件重新安装一次

原文链接：[https://blog.csdn.net/huariylee/article/details/52661290](https://blog.csdn.net/huariylee/article/details/52661290)