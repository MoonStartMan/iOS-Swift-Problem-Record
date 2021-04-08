# Swift-guard语法

## if let

``` swift

func doSomething(str: String?) {
	let v :String! = str
	if v != nil
	{
		//	use v to do something
	}
}

```

swift中因为有optional,经常需要判断是否为空。假如没有 if let，大致写成上面的样子，有了if let，可以改写成

``` swift

func doSomething(str: String?) {
	if let v = str
	{
		//	use v to do something
	}
}

```

上面两段代码的控制流是一样的。对照着,可以看出if let的写法更加简介方便。

## guard

假如if中出现的代码很长，我们写代码时可以将错误情况先返回。比如:

``` swift

func doSomething(str:String?) {
	let v:String! = str
	if v == nil
	{
		return
	}
	//	use v to do something
}

```

guard可以改写成:

``` swift

func doSomething(str: String?) {
	guard let v = str else { return }
	//	use v to do something
}

```

## 总结

与if语句相同的是，guard也是基于一个表达式的布尔值去判断一段代码是否该被执行。与if语句不同的是，guard只有在条件不满足的时候才会执行这段代码。你可以把guard近似的看做是Assert,但是你可以优雅的退出而非崩溃。