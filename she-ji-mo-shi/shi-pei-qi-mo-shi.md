# 适配器模式

## 1、相关概念

### 1.1 定义

将一个接口转换成客户希望的另一个接口，使接口不兼容的类可以一起工作

### 1.2 类适配器

#### 1.2.1 定义

将适配者API转换成目标类API

#### 1.2.2 UML

![](../.gitbook/assets/image%20%2849%29.png)

图画错了，Adapter继承Adaptee，实现Target接口

### 1.3 对象适配器

#### 1.3.1 定义

也是把，使用委托关系连接到Adaptee

#### 1.3.2 UML图

![](../.gitbook/assets/image%20%2850%29.png)

（图画错了，是依赖关系，Adapter持有Adaptee的引用）

## 2、应用

### 2.1 listView

![](../.gitbook/assets/image%20%2813%29.png)



