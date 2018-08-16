# Socket



### 基础知识

1. ip地址和端口号
2. tcp/udp
   1. tcp：顺序无差错
   2. udp：1）效率高；2）不需要
   3. URL

![](../../.gitbook/assets/image%20%2831%29.png)

### Socket

#### 创建socket实例

#### 客户端链接

![](../../.gitbook/assets/image%20%2832%29.png)

![](../../.gitbook/assets/image%20%2834%29.png)

#### 服务端链接

![](../../.gitbook/assets/image%20%2820%29.png)

#### 总结

![](../../.gitbook/assets/image%20%2865%29.png)

## 阻塞IO

### java的IO接口

![](../../.gitbook/assets/image%20%2814%29.png)

* inputStream
* reader
* file
* socket

### 阻塞式IO的通信模型

1、阻塞会增加CPU负担

2、即BIO block，BIO 在数据写入或者从InputStream读取都会阻塞线程

