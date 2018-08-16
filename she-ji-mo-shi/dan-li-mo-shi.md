# 单例模式

## 1、实现方式

懒汉式/饿汉式

### 1.1 静态内部类方式实现

```text
public class SingleTon{
  private SingleTon(){}
 
  private static class SingleTonHoler{
     private static SingleTon INSTANCE = new SingleTon();
 }
 
  public static SingleTon getInstance(){
    return SingleTonHoler.INSTANCE;
  }
}
```

### 1.2 DCL\(Double Check Lock\)

## 2、应用场景分析

### 2.1 application



