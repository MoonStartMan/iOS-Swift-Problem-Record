# swift内存管理-weak与unowned

## weak

日常开发中,我们经常会用weak来标记代理或者在闭包中使用它来避免引用循环。

``` swift

weak var delegate: SomeDelegate?

lazy var someClosure: () -> Void = { [weak self] in 
	guard let self = self else { return }
	self.balabala
}

```

当我们赋值给一个被标记 weak 的变量时，它的引用计数不会被改变。而且当这个弱引用变量所引用的对象被释放时，这个变量将被自动设为 nil。这也是弱引用必须被声明为 Optional 的原因。

## unowned

和weak相同,unowned也可以在不增加引用计数的前提下，引用某个类实例。

``` swift

unowned let someInstance: SomeClass

lazy var someClosure: () -> void = { [unowned self] in
	self.balabala
}

```

在使用unowned时，我们不需要将变量声明为Optional。

需要注意的是。对于被 unowned 标记的变量，即使它的原来引用已经被释放，它仍然会保持对被已经释放了的对象的一个 "无效的" 引用，它不是 Optional ，也不会被指向 nil。所以，当我们试图访问这样的 unowned 引用时，程序就会发生错误。

