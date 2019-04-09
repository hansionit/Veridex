
> 在Android P版本,Google对非SDK接口增加了管控
> 
> SDK接口指的是Android官方开发文档中声明的方法,即[文档地址](https://developer.android.google.cn/reference/packages) 中所能查询到的API,除了这些,其他的API都是非SDK接口



在Android P版本,非SDK接口分类

* light grelist 浅灰名单 
* dark greylist 深灰名单
* blacklist 黑名单

在Android Q版本,为了更精准的控制与兼容,非SDK接口分类

* whitelist 白名单 可随意调用
* greylist 灰名单  警告
* greylist-max-o  targetSDK>=O时不允许调用,targetSDK<O时警告
* greylist-max-p targetSDK>=P时不允许调用,targetSDK<P时警告
* blacklist 黑名单 不允许调用

## 如何检测

Google提供了一个静态检测工具veridex[下载地址 需科学上网](https://android.googlesource.com/platform/prebuilts/runtime/+/master/appcompat) 

由于网络的原因,很多朋友无法下载,所以我将其上传到仓库,若能打开网页,推荐下载最新版本


## 使用方法

根据个人所使用的系统进行区分使用,进入系统对应的目录,输入:
> ./appcompat.sh --dex-file=test.apk --imprecise


---



### appcompat.sh

Given an APK, finds API uses that fall into the blacklist/greylists APIs.

NOTE: appcompat.sh is still under development. It can report
API uses that do not execute at runtime, and reflection uses
that do not exist. It can also miss on reflection uses.

#### Instructions

Note that only 64-bit binaries are provided. 32-bit systems are not supported.

##### Linux x64

Download veridex-linux.zip, unzip the file and run with:
> ./appcompat.sh --dex-file=test.apk

##### macOS

Download veridex-mac.zip, unzip the file and run with:
> ./appcompat.sh --dex-file=test.apk

##### Windows 10

Native Windows binaries are not provided, but the Linux binaries can be executed
with Windows Subsystem for Linux (WSL).

Follow the instructions at [this
link](https://docs.microsoft.com/en-us/windows/wsl/install-win10) and install
Ubuntu distribution when given the choice. Once installed, launch an Ubuntu
terminal and follow instructions for Linux.