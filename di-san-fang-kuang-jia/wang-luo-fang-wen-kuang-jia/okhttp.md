# OkHttp

## 1、使用

1. OkHttpClient 
2. Request  Builder模式，分发http请求
3. Response   创建请求Call，拦截器
   1. execute
   2. enqueue

## 2、原理

OkHttp的底层是通过Java的Socket发送HTTP请求与接受响应的\(这也好理解，HTTP就是基于TCP协议的\)，但是OkHttp实现了**连接池**的概念，即对于同一主机的多个请求，其实可以**共用一个Socket连接**，而不是每次发送完HTTP请求就关闭底层的Socket，这样就实现了连接池的概念。而OkHttp对Socket的读写操作使用的OkIo库进行了一层封装。

作者：马伟奇 链接：[https://www.jianshu.com/p/9ed2c2f2a52c](https://www.jianshu.com/p/9ed2c2f2a52c) 來源：简书 

