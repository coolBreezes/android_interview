# BroadcastReceiver

## 1、内部实现机制

1. 自定义广播接收者BroadcastReceiver，并复写onReceive\(\)方法
2. 通过Binder机制向AMS\(Activity Manager Service\)进行注册
3. 广播发送者通过Binder机制向AMS发送广播
4. AMS查找符合相应条件\(IntentFilter/Permission等\)的BroadcastReceiver，将广播发送到BroadcastReceiver\(一般情况下是Activity\)相应的消息循环队列中
5. 消息循环队列执行拿到的广播，回调onReceive\(\)方法

## 2、LocalBroadcastManager实现机制

1. 使用Handler来实现 高效、安全 它的sendBroadcast\(\)方法是通过handler发送一个message来实现

### 2.1 使用

![](../../.gitbook/assets/image%20%281%29.png)



