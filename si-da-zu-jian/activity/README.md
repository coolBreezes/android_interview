# Activity

## [1.activity的启动模式](https://blog.csdn.net/CodeEmperor/article/details/50481726)

### 1.1 Standard 标准模式

1）特点：每次重新创建Activity

### 1.2 SingleTop 栈顶复用

1）特点：若重启的Activity刚好在栈顶，会复用栈顶Activity，不会重新创建实例，但生命周期为  [**onPause-&gt;onNewIntent-&gt;onResume**](https://blog.csdn.net/qq_33505655/article/details/80242327)\*\*\*\*

2）场景： **适合接收推送通知启动的内容显示页面**，接收到消息后弹出Activity，如果一次来10条消息，总不能弹10个Activity

### 1.3 SingleTask 栈内复用

1）特点：检测栈内是否存在，若存在，将其置于栈顶（**调用newIntent\(\)**）,**其上面的Activity都移除销毁**，若不存在则重新创建。

2）场景：程序主界面（入口）

### 1.4 SingleInstance 全局唯一模式

1）特点：全局唯一

2）场景：适合需要与程序分离开的页面，比如闹铃提醒，将闹铃提醒和闹铃设置分离（SingleInstance不要设置为中间页面）

