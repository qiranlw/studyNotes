# 设计模式之禅

## 设计原则

#### 单一职责原则

#### 里氏替换原则

#### 依赖倒置原则

#### 接口隔离原则

#### 迪米特法则

#### 开闭原则

## 单例模式

单例模式：确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例。

```java
// 饿汉模式
public class Singleton {
	private static final Singleton instance = new Singleton();
	private Singleton(){
		//do something
	}
	public static Singleton getInstance(){
		return this.instance;
	}
	public static void doSomething(){
	}
}

// 懒汉模式
public class Singleton {
	private static final Singleton instance = null;
	private Singleton() {
		// do something
	}
	public static Singleton getInstance() {
		if (instance == null) {
			sychronized (Singletion.class) {
				if(instance == null) {
					instance = new Singleton();
				}
			}
		}
		return instance;
	}
}

// 内部类模式
public class Singleton {
	private Singleton() {
		// do something
	}
	private static class SingletonHolder {
		private static Singleton instance = new Singleton();
	}
	public static Singleton getInstance() {
		return SingletonHolder.instance;
	}
}

// 枚举模式
public enum Singleton {
	uniqueInstance;
}
```
#### 优点
* 减少内存开支
* 减少系统性能开销
* 避免资源的多重占用
* 设置全局访问点，优化和共享资源访问

#### 缺点
* 没有接口，扩展困难
* 对测试不利
* 与单一职责原则有冲突

#### 应用场景
* 要求生成唯一序列号的环境
* 在整个项目中需要共享访问点或共享数据，如计数器
* 创建一个对象需要消耗的资源过多
* 需要定义大量静态常量和静态方法的环境

#### 注意事项
* 注意线程同步问题
* 单例对象不能被复制，不能实现 `Cloneable` 接口

#### 扩展
* 生成固定数量类的实例

## 工厂方法模式

