# IntentService

## 1、原理

1. 多次启动IntentService，不会重复创建多个服务
2. IntentService会顺序执行
3. 在onHandleIntent 处理异步耗时任务

