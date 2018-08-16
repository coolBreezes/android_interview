---
description: 'refer：https://www.cnblogs.com/zyanrong/p/5661114.html'
---

# App启动过程

## 1、Android启动过程

1.Boot Loader （初始化硬件设备、建立内存空间的映射图）

2.Linux内核初始化，启动init进程 （祖先进程）

3.fork出Zygote进程 （所有java进程的父进程）

4.fork出System Server进程（属于Framework层），会初始化AMS（ActivityManagerServices），创建上下文，创建ActivityThread以及开启各种服务

5.之后，开启系统的启动Launcher程序，完成系统界面的加载与显示。

## 2、App启动过程

* 当我们点击桌面的APP图标时，Launcher进程会采用Binder的方式向AMS发出startActivity请求
* AMS在接收到请求之后，就会通过Socket向Zygote进程发送创建进程的请求
* Zygote进程会fork出新的子进程（APP进程）
* 之后APP进程会再向AMS发起一次请求，AMS收到之后经过一系列的准备工作再回传请求。
* APP进程收到AMS返回的请求后，会利用Handler向主线程发送LAUNCH\_ACTIVITY消息
* 主线程在收到消息之后，就创建目标Activity，并回调onCreate\(\)/onStart\(\)/onResume\(\)等方法，UI渲染结束后便可以看到App主界面 

