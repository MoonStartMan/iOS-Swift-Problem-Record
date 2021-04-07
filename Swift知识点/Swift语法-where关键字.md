# Swift语法-where关键字

1、在集合遍历时使用where，条件为真时执行代码块，为假时不执行代码块。

``` swift

let array = [0, 1, 2, 3, 4, 5, 6]

//	使用switch遍历

array.forEach {
	switch $0 {
	case let x where x > 3:	//	where相当于判断条件
		print("后半段")
	default:
		print("默认值")
	}
}

//	使用for in遍历
for value in array where value > 2 {
	print(value)	//	输出3 4 5 6
}

for (index, value) in array.enumerated() where index > 2 && value > 3 {
	print("下标:\(index),值:\(value)")
}
```

输出

``` 

默认值
默认值
默认值
默认值
后半段
后半段
后半段
3
4
5
6
下标:4, 值:4
下标:5, 值:5
下标:6, 值:6

```

2、在补充异常的do/catch里使用

``` swift

enum SomeError: Error {
	case error1(Int)
	case error2(String)
}

func methodError() throws {
	throw SomeError.error1(1)
}

do {
	try methodError()
} catch SomeError.error1(let param) where param > 2 {	//	捕获异常时要判断参数
	print(param)
} catch {
	print("默认异常处理")
}
```

3、协议使用where，只有基类实现了当前协议才能添加扩展。换个说法，多个类实现了同一个协议，该语法根据类名分别为这些类添加扩展，注意是分别(以类名区分)！！！

``` swift

protocol SomeProtocol {
	func someMethod()
}

class A: SomeProtocol {
	let a = 1
	
	func someMethod() {
		print("call someMethod")
	}
}

class B {
	let a = 2
}

//	基类A继承了SomeProtocol协议才能添加扩展
extension SomeProtocol where Self: A {
	func showParamA() {
		print(self.a)
	}
}

//	反例，不符合where条件
extension SomeProtocol where Self: B {
	func showParamA() {
		print(self.a)
	}
}

let objA = A()
let objB = B()	//	类B没实现SomeProtocol，所有没有协议方法
objA.showParamA()	//	输出1
```

## 小结

where关键字可以用在集合遍历、switch/case、协议中;Swift3时if let和guard场景的where已经被swift4的逗号取代,例如 **if let a=param, a>10(前者需要判断是否为nil,后者相当于where条件) **