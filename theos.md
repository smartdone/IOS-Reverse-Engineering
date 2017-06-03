# Theos

---

## 安装Theos

1. 安装xcode，如果安装了多个xcode就用`sudo xcode-select -s /Applications/xcode.app/Contents/Developer`来选择默认的xcode

2. 下载theos

   从github上面下载theos，操作如下:

   ```shell
   export THEOS=/opt/theos
   sudo git clone https://github.com/theos/theos.git
   ```

3. 配置ldid

   ldid是专门用来签名ios可执行文件的工具，用以在越狱的ios中取代xcode自带的codesign，从[http://joedj.net/ldid](http://joedj.net/ldid)下载ldid，然后把它放到theos的bin目录下面，并且赋予可执行的权限

4. 配置dpkg

5. 配置环境变量

   配置环境变量THEOS，将theos的bin加到PATH环境变量中
   ```shell
   export THEOS=theos的路径
   export PATH=$PATH:$THEOS/bin
   ```

6. 测试是否装成功

   在终端执行`nic.pl`如果出现如下图就表示安装成功了  
   ![nic.pl](./img/theos/nictest.png)

## 创建工程

1. `nic.pl`
2. 输入11选择iPhone/tweak
3. `Project Name (required):`输入工程名
4. `Package Name [com.yourcompany.test]:`输入报名
5. `Author/Maintainer Name[xxxx]:`输入作者名字
6. `[iphone/tweak] MobileSubstrate Bundle filter [com.apple.springboard]:`输入作用的对象的bundle indentfier
7. 输入安装完之后需要重启的应用，以进程名称表示

> 创建完成之后，目录结构如下图。Makefile,Tweak.xm,control,xxx.plist文件

![](./img/theos/files.png)

### Makefile

Makefile文件指定工程用到的文件、框架、库等信息，将整个过程自动化，Makefile文件的内容如下：

```Makefile
include $(THEOS)/makefiles/common.mk

TWEAK_NAME = test
test_FILES = Tweak.xm

include $(THEOS_MAKE_PATH)/tweak.mk

after-install::
	install.exec "killall -9 SpringBoard"
```

`TWEAK_NAME = test`是tweak的名字，就是用nic.pl创建工程的时候指定的"Project Name"，跟control文件中的“Name”对应，不要更改。

`test_FILES = Tweak.xm`是指tweak包含的源文件"不包括头文件"，多个文件用空格分隔

`include $(THEOS_MAKE_PATH)/tweak.mk`根据不同的theos类型，通过include命令指定不同的mk文件

`install.exec "killall -9 SpringBoard"`在安装之后杀掉SpringBoard好让cydiaSubstrate加载对应的dylib，和Android类似，我猜可能ios那些应用的进程可能都是SpringBoard给fork出来的，所以把它杀掉，重新打开的应用就会被注入dylib，