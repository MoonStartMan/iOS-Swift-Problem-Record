# Swift - mutating关键字

使用 **mutating** 关键字修饰方法是为了修饰方法是为了能在该方法中修改struct或是enum的变量,在设计接口的时候,也要考虑使用者程序的扩展性。所以要多考虑使用mutating来修饰方法。

首先,先定义一个 **protocol** 

``` swift

protocol ExampleProtocol {
	var simpleDescription: String { get }
	mutating func adjust()
}

```

在上面定义了一个 **ExampleProtocol** ,接下来我们写一个class来遵守这个协议

``` swift

class SimpleClass: ExampleProtocol {
	var simpleDescription: String = "A very simple class"
	var anotherProperty: Int = 110
	//	在 class 中实现带有 mutating 方法的接口时,不用 mutating 进行修饰。因为对于 class 来说,类的成员变量和方法都是透明的, 所以不必使用 mutating 来进行修饰
  func adjust() {
  	simpleDescription += "Now 100% adjusted"
  }
}
//	打印结果
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription
```

在 struct 中实现协议 ExampleProtocol

``` swift

struct SimpleStruct: ExampleProtocol {
	var simpleDescription: String = "A simple structure"
	mutating func adjust() {
		simpleDescription += "(adjusted)"
	}
}

```

在 ** enum ** 中实现协议 ** ExampleProtocol **

``` swift

enum SimpleEnum: ExampleProtocol {
	case First, Second, Third
	var simpleDescription: String {
		get {
			switch self {
			case .First:
				return "first"
			case .Second:
				return "second"
			case .Third:
				return "third"
			}
		}
		set {
			simpleDescription = newValue
		}
	}
	mutating func adjust() {
		
	}
}

```

## 错误信息

如果将 ** ExampleProtocol ** 中修饰方法的 ** mutating **去掉,编译器会报错说没有实现protocol。如果将 ** struct ** 中的 ** mutating ** 去掉,则报错不能更改结构体的成员。