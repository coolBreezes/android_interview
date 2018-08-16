# HashMap

## refer:

1. 干货：HashMap的工作原理解析 [https://juejin.im/post/5a7592f4f265da4e8d42ded2](https://juejin.im/post/5a7592f4f265da4e8d42ded2)

## 1、概念

### 1.1 是什么

    数组 + 链表

1. 默认长度为16，默认负载因子为0.75

## 2、原理

### 2.1 数组逻辑结构部分

    **index = hash\(key\)%len**  
注：index是数组的下标，key是HashMap元素的key值，len是数组的长度。 作者： 链接：[https://www.imooc.com/article/37043](https://www.imooc.com/article/37043) 来源：慕课网

返回的hashCode用于找到bucket位置来储存Entry对象。



### 2.2 解决Hash冲突

根据hash函数，找到bucket位置，

发生冲突，根据equals\(\)方法，找到对应的Entry

## [3、相关面试题](https://www.cnblogs.com/lchzls/p/6714474.html)

### 3.1 hashmap的工作原理

