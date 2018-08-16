# AsyncTask

## 1、是什么

本质上是一个封装了线程池和handler的异步框架  
通过handler在主线程和工作线程处理异步消息



## 2、使用方法

   3个参数

   5个方法

### 2.1 3个参数

1. params
2. progress
3. result

### 2.2  5个方法

1. onPreExecute\(\)
2. doInBackgroud\(\) publishProgress\(\)
3. onProgressUpdate\(\) 调用publishProgress\(\)时自动调用
4. onPostExecute\(\)
5. 串行 execute\(\)

## 3、机制原理

1. 本质是一个静态的线程池

## 4、注意事项

### 4.1 内存泄漏

1. 静态内部类
2. onDestroy\(\) 中  asyncTask.cancel\(\)

### 4.2 生命周期

### 4.3 结果丢失

