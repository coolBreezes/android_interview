# 多线程

## 多线程的创建

### thread/runnable

### 两种启动方式的区别

### start/run方法的区别

如果执行start方法，则会在主线程中重新创建一个新的线程，等得到cpu的时间段后则会执行所对应的run方法体的代码。

## 线程间通信

### synchronized 

#### 对象锁

#### 进程间通信

#### 与volatile

都是从主内存去获取变量值，

#### 与lock

lock需要开始和结束设置lock和unlock

synchronized：悲观锁  
lock：CPU乐观锁机制

### sleep/wait

### wait/notify机制

## 线程池

### 好处

* 降低资源消耗，避免频繁的创建/消耗线程带来的开销
* 提高响应速度
* 提高线程的可管理性，使用线程池，可以做到统一分配

### ThreadPoolExecutor

### 线程池的工作流程

![](../.gitbook/assets/image%20%2827%29.png)



## [ThreadLocal](https://blog.csdn.net/imzoer/article/details/8262101)

ThreadLocal提供了set和get访问器用来访问与当前线程相关联的线程局部变量。

Thread中的threadlocals变量是在ThreadLocal对象中调用createMap函数来初始化的。



