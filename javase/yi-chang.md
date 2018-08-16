# 异常

## 1、异常体系

## 2、使用

### 2.2 异常处理的原理

![](../.gitbook/assets/image%20%288%29.png)

### 2.3 异常处理的流程

1）关闭了虚拟机，finally代码块不会被执行

![](../.gitbook/assets/image%20%2856%29.png)

2）finally代码块在return之前执行

![](../.gitbook/assets/image%20%2852%29.png)

3）传值，不能通过重新赋值改变try中的return值

![](../.gitbook/assets/image%20%2847%29.png)

4）

![](../.gitbook/assets/image%20%285%29.png)

5）小结

![](../.gitbook/assets/image%20%2843%29.png)

## 3、常见面试题

### 3.1 检查和非检查异常

### 3.2 throw/throws

1. throw 是抛出异常
2. throws 方法可能抛出异常的声明（**声明可能会出现的异常**）

#### 3.3 final、finalize、finally



