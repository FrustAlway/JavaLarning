# Java中的设计模式

### 概念

**含义**

按照已有的项目模式,进行项目搭建,称已有的项目模式为设计模式

**分类**

```
一共23种设计模式
1.代理设计模式
2.工厂设计模式----生产出来的长得都一样
3.装饰设计模式---核心类库
4.单例设计模式---框架部分常用:一个对象只能实例化一次
5.模版设计模式
6.适配器模式
```

### **单利设计模式**

**特点:**

```
构造器私有化----private
本类中一定要实例化对象一次
对外一定是提供一个获取本类对象的方法
```

#### **两种表现形式————饿汉式  和 懒汉式**

**饿汉式**（无论是否使用本类，都贱这个对象创建出来）

只要你想获取定义的对象,代码就会new一次,而且new的名字是一样的,下面代码中,就是es

```
静态的获取,一定要new一次(一定要实例化对象一次)
private static Esingleton es = new Esingleton();
构造器私有化
private Esingleton(){}
对外提供的能够获取本来对象的方法 
public static Esingleton getEsingleton(){
    return es;
}
```

主函数中

```
Esingleton es = Esingleton.getEsingleton();
System.out.print(es)------打印的地址,而且每次打印的地址都是一样的,说明是实例化对象实例化一次,
```

**懒汉式(掌握)**（不会主动创建对象，什么时候使用到了该对象才会创建这个对象）

```
private static lazSingleton ls;
private lanSingleton(){}

同步:如果是多线程操作,更安全,(多人同时操作一个资源) 
(死锁,PV操作)
public static synchronized lanSingleton getlanSingleton(){
    //额外一次的判断,是否为空 
    if(ls == null){
        ls = new lanSingleton();
    }
    return ls;
}
```

#### 懒汉式和饿汉式的区别

```
懒汉式:
	多线程操作,更安全,体现synchronized
饿汉式:
	单线程操作,更加快捷，用户体验更好

线程需要额外的操作才可以进行,这个时候的多线程和单线程才是正常的说法
```



## 装饰设计模式(理解)

**含义**

```java
在不改变原有类结构的(类成员 和 类的设计结构)基础上,提供更强大的操作功能,一种类的设计模式
```