# TCP/IP网络模型

## 1、物理层

## 2、链接层

### 2.1 链接层的协议

## 3、网络层

## 4、传输层

### 4.1 TCP

    Transmission Control Protocol 传输控制协议

    有连接，可靠

    HTTP/FTP/SMTP

### 4.2 UDP

    User Datagram Protocol 用户数据报协议

    无连接，不可靠

    DNS/DHCP

### 4.3 TCP三次握手，四次挥手

refer:[https://www.jianshu.com/p/a1ebc61ce141](https://www.jianshu.com/p/a1ebc61ce141)

#### 4.3.1 三次握手

1. client发送同步信号，并随机生成一个seq=J序号， 进入SYN\_SENT状态，等待Server确认
2. server确认收到client的同步信号ack=J+1，并向服务端发送同步信号， 进入SYN\_REVD状态
3. client收到确认后，... 双方进入ESTABLISHED状态

![](../.gitbook/assets/image%20%289%29.png)

#### 4.3.2 四次挥手

![](../.gitbook/assets/image%20%2853%29.png)

#### 4.3.3 为什么建立连接是三次握手，而关闭连接却是四次挥手呢？

这是因为服务端在LISTEN状态下，收到建立连接请求的SYN报文后，把ACK和SYN放在一个报文里发送给客户端。而关闭连接时，当收到对方的FIN报文时，仅仅表示对方不再发送数据了但是还能接收数据，己方也未必全部数据都发送给对方了，所以己方可以立即close，也可以发送一些数据给对方后，再发送FIN报文给对方来表示同意现在关闭连接，因此，己方ACK和FIN一般都会分开发送。

作者：JackJiang2011 链接：[https://www.jianshu.com/p/a1ebc61ce141](https://www.jianshu.com/p/a1ebc61ce141) 來源：简书 

