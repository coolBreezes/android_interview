# Handler

## 1、原理

Looper开启循环，不断地从MessageQueue中获取Message，交由Hander，以handleMessage方法来处理消息

## 2、内存泄漏

### 1.1 原因

匿名内部类持有外部类的引用

1. 设为静态内部类
2. onDestroy\(\)中 调用 removeCallback\(\)

