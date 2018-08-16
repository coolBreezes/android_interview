# Retrofit

refer：

1.从架构角度看Retrofit的作用、原理和启示

{% embed data="{\"url\":\"https://www.jianshu.com/p/f57b7cdb1c99\",\"type\":\"link\",\"title\":\"从架构角度看Retrofit的作用、原理和启示\",\"description\":\"Retrofit是squareup公司的开源力作，和同属squareup公司开源的OkHttp，一个负责网络调度，一个负责网络执行，为Android开发者提供了即方便又高效的网络访问框架。 不过...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://cdn2.jianshu.io/assets/apple-touch-icons/152-bf209460fc1c17bfd3e2b84c8e758bc11ca3e570fd411c3bbd84149b97453b99.png\",\"width\":152,\"height\":152,\"aspectRatio\":1}}" %}

2.retrofit入门介绍

[https://www.jianshu.com/p/308f3c54abdd ](https://www.jianshu.com/p/308f3c54abdd%20)

## 1、使用场景

1. 定义接口
2. 依次获得Retrofit对象、接口实例对象、网络工作对象
   1. 首先，新建一个retrofit对象；
   2. 然后，根据上一步的接口，实现一个retrofit加工过的接口对象（代理对象）；
   3. 最后，调用接口函数，得到一个可以执行网络访问的网络工作对象。
3. 访问网络数据

```text
//retrofit对象
Retrofit retrofit=new Retrofit.Builder()
.baseUrl(Config.DOMAIN)
.addConverterFactory(GsonConverterFactory.create())
.addCallAdapterFactory(RxJava2CallAdapterFactory.create())
.build();

//用retrofit加工出对应的接口实例对象
INetApiService netApiService= retrofit.create(INetApiService.class);
···
//调用接口函数，获得网络工作对象
Flowable<BizEntity> callWorker= netApiService.getBizInfo("id001");

作者：蓝灰_q
链接：https://www.jianshu.com/p/f57b7cdb1c99
來源：简书
```

## 2、注解

1. 网络请求
2. 标记类
   1. FormUrlEncoded
   2. MultiPart
   3. Streaming
3. 参数类
   1. Header、Headers
   2. Field、FieldMap
   3. Part、PartMap
   4. Path、Query、QueryMap、Url

## 3、实现原理

### 3.1  Q：Retrofit的实现原理？

（思路：先介绍功能，实现这一目标需要哪些组件，思考为什么要这样去设计，

是什么（功能）——&gt; 要什么（目标）——&gt; 为什么（弄懂）——&gt; 有什么（该怎么做））

    （Retrofit是对OkHttp的简单封装）

    **Retrofit本身不直接做网络请求，而是按照接口定义，自动定制一个能做网络请求的对象**（Call网络工作对象）。

（这个接口不是用来获取数据，而是用来作为生产对象的接口），**这个接口相当于一个工厂，接口中每个函数的返回值不是网络数据，而是一个能进行网路请求的工作对象**，我们要先调用函数获得工作对象，再用这个工作对象去请求网络数据。

    可以看出**Retrofit的意义在于，它能根据你的接口定义，灵活的生成对应的网络工作对象**，然后我们再择机去调用这个对象访问网络数据。

    所以，**Retrofit的目标应该就是为了避免为网络访问编写大量的配套代码**。为了实现这一目标，Retrofit需要分析哪些是不变的，哪些是易变的，然后分别处理。

   由于Retrofit提供网络访问的工作对象，又是服务于具体业务，所以可以分网络访问和具体业务两部分来分析。

#### 1）、网络访问的不变性

对于网络访问来说，不变的是一定有一个实现网络访问的对象，Retrofit选用了自家的OkHttpClient，不过为了把Retrofit和OkHttp两个项目**解耦**合，Retrofit根据**依赖倒置原则**，定义了Retrofit自己的Call即retrofit2.call，并定义了操作网络请求的OkHttpCall。依赖于抽象，而不依赖具体。

#### 2）、网络访问的易变性

对于网络访问来说，易变的是网络访问的url、请求方式（get/post等）、Http请求的Header设置与安全设置等，以及返回的数据类型。

针对易变的url和请求方式，Retrofit使用了**方法注解**的方式，可读性良好，扩展性优异，但这需要实现对接口函数中注解的解析，这样就有了**ServiceMethod**。  
 针对Http请求的各种设置，其实Retrofit没做什么，因为Retrofit使用的OkHttp有**拦截器**机制，可以应付这种变化。  
 针对返回的数据类型，由于目标数据类型与业务有关，是不确定的，Retrofit无法提供一个万能的转换类，所以Retrofit提供了扩展接口，允许开发者自己定义**ConverterFactory和Converter**，去实现潜在的数据类型转换。

#### 3）、具体业务的不变性

 对于具体业务来说，不变的是一定要有一个Call网络工作对象，所以Retrofit可以有一个生产对象的机制（像工厂一样、构造者模式）

#### 4）、具体业务的易变性

对于具体业务来说，易变的就是这个Call网络工作对象的类型，不仅有CallBacl回调、可能还有Flowable工作流、或者其他潜在的对象类型。

针对这种Call对象的易变性，Retrofit也是无法提供一个万能的实现类，所以也是提供了扩展解耦，允许开发者自己定义**CallAdapterFactory和CallAdapter**，去实现潜在的Call类型转换。

因为这种Call对象的生产需要有大量的配套代码，为了简化代码，Retrofit使用**动态代理**来生产这个对象。

最后，因为需要处理的方法和对象太多太复杂，需要使用**建造者模式**来把建造过程和使用过程分离开。

### 3.2 借鉴与启示

1. 万物皆对象  网络访问后，回调数据是个对象；网络访问本身也是个对象。
2. 依赖倒置  哪怕是使用自家的OkHttp，哪怕底层调用的始终是OkHttpClient，也需要依赖一个抽象的retrofit2.Call接口，依赖于抽象，而不是依赖于具体。
3. 单一职责  类的职责需要维持单一，流程需要但是超出自己职责的功能，去调用相关的类实现，比如OkHttpClient和ServiceMethod的各自职责与调用关系。
4. 迪米特法则  内部实现再复杂，对于外部调用者也只展示他需要的那些功能，例如Retrofit。
5. 自动&gt;人工  动态代理的使用，可以用自动生成的模板代码，减轻人工编写配套代码的工作量，成本更低，风险更低。
6. 利用工厂类开放扩展  对于流程确定，但方法不能确定的，利用工厂类，对调用者开放扩展能力。
7. 利用多个工厂类组成扩展列表  如果1个工厂类不能实现兼得，何不设置一个工厂类列表，在多个工厂类中，看哪个工厂类能解决问题。
8. 利用建造者模式把建造和使用分离  这样使用者不需要关系复杂的建造过程，例如Retrofit和ServiceMethod。
9. 利用外观模式减少对复杂子系统的操作  虽然有复杂的子系统协同工作，调用者只需要调用最外层的Retrofit即可。
10. 其他  开放封闭、接口隔离、里式替换、静态代理等设计原则或设计模式都有体现也都很熟悉了，就不再啰嗦。



