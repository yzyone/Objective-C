
# 使用Sublime Text开发Objective-C #

## 前言 ##

随着iPhone的热卖，开发iPhone APP所使用的Objective-C，也慢慢成为了热门的程序语言之一。本篇文章介绍如何在Windows操作系统中，透过Sublime Text这个工具来开发Objective-C，让没有预算添购Mac设备的开发人员，也能够学习Objective-C的语法。主要为自己留个纪录，也希望能帮助到有需要的开发人员。

前言01

## 安装Python ##

必须要先安装Python，接着安装GNUstep，才能在Windows操作系统中编译Objective-C。而Python的安装程序，可以从Python官网下载。

https://www.python.org/

安装Python01

安装Python02

## 安装GNUstep ##

装完Python，接着安装GNUstep，之后就能透过GNUstep来编译Objective-C。GNUstep的安装程序，可以从 GNUstep官网下载，但为了简化安装步骤，透过下列网址取得包装过的GNUstep压缩文件「GNUstep.7z」，直接解压缩至C:底下即完成安装。

https://github.com/sol-prog/ClangGNUstepObjective-CforWindows

安装GNUstep01

安装GNUstep02

但因为是透过GNUstep压缩文件的方式来进行安装，所以必须要手动将「C:\GNUstep\bin」、「C:\GNUstep\GNUstep\System\Tools」这两个GNUstep路径加入Windows系统变量Path之中。(记得要重新启动)

安装GNUstep03

GNUstep安装完毕之后，还需要将下列档案「Objective-c.gnustep-build.bat」,加入GNUstep的目录路径「C:\GNUstep\msys\1.0\」，用以告知GNUstep如何编译Objective-C。

点此下载：Objective-c.gnustep-build.bat

安装GNUstep04

## 安装Sublime Text ##

装完GNUstep，接着安装Sublime Text，之后就能透过Sublime Text来编译Objective-C程序代码。而Sublime Text的安装程序，可以从Sublime Text官网下载。

http://www.sublimetext.com/

安装SublimeText01

安装SublimeText02

Sublime Text安装完毕之后，还需要将下列档案「Objective-c.sublime-build」，加入Sublime Text的目录路径「C:\Users\%USERNAME%\AppData\Roaming\Sublime Text 2\Packages\User」，用以告知Sublime Text使用GNUstep来编译Objective-C。

点此下载：[Objective-c.sublime-build](http://files.dotblogs.com.tw/clark/1412/201412316488474.rar)

安装SublimeText03

## 开发Objective-C ##

完成安装步骤后，开启Sublime Text,输入下列Objective-C程序代码，并且储存为扩展名为「.m」的档案。(档案路径不可包含中文)

```
#include <Foundation/Foundation.h>
 
int main(){
    @autoreleasepool{
        NSLog( @"\n\n Hello Objective-C by Clark \n\n");
    }
    return 0;
}
```

接着在系统选单的「\Tool\Build System\」中，勾选使用Objective-C。

开发01

后续就可以透过快捷键「Ctrl+B」，来编译并且执行Objective-C。

开发02

## 参考数据 ##

[Clang and Objective-C on Windows - Solarian Programmer](https://solarianprogrammer.com/2012/03/21/clang-objective-c-windows/)

[在Windows上写Objective-C程序 - 叶难](http://yehnan.blogspot.tw/2012/03/windowsobjective-cgnustepclangllvm.html)

转载于:https://www.cnblogs.com/clark159/p/4194941.html