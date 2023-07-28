# DispatchSemaphore

## 什么是DispatchSemaphore

DispatchSemaphore是GCD框架中的一个类，用于管理信号量。

信号量是一个整数值，它可以用来控制并发操作的数量。当一个线程需要访问一个受信号量保护的资源时，它会尝试获取信号量。如果信号量的值大于0，线程可以继续执行，并将信号量的值减1。如果信号量的值为0，线程将被阻塞，直到有其他线程释放了信号量。

## DispatchSemaphore方法

DispatchSemaphore类提供了以下几个方法

+ int(value: Int): 创建一个信号量对象，并指定初始值
+ wait(): 尝试获取信号量，如果信号量的值大于0，则将其减1；如果信号量的值为0，则线程将被阻塞。
+ signal(): 释放一个信号量，将其值加1.如果有其他线程正在等待获取信号量，其中一个线程将被唤醒并获得信号量。

DispatchSemaphoreWrapper是一个对DispatchSemaphore的封装，它简化了信号量的使用，并提供了更方便的语法。

## 实例代码

下面是一个使用DisPatchSemaphore的实例代码

``` swift

let semaphore = DispatchSemaphore(value: 2)
DispatchQueue.global().async {
	semaphore.wait()
	//	访问受信号量保护的资源
	//	...
	semaphore.signal()
}

```