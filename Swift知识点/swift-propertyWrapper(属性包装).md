# swift-propertyWrapper(属性包装)

属性包装器，用来修饰属性，它可以抽取关于属性重复的逻辑来达到简化代码的目的

## 使用属性包装器

通过 ** @propertyWrapper **来标识structure、enumeration、class

### 要求

+ 必须使用属性 @propertyWrapper 进行定义
+ 必须具有 wrappedValue 属性

## 代码部分

``` swift

@propertyWrapper
struct TwelveOrLess {
	private var number: Int
	
	init() {
		self.number = 0
	}
	
	var wrappedValue: Int {
		get {
			number
		}
		set {
			number = min(newValue, 12)
		}
	}
}

```

``` swift

struct SmallRectangle {
	@TwelveOrLess var height: Int
	@TwelveOrLess var width: Int
}

var rectangle = SmallRectangle()
print(rectangle.height)

rectangle.height = 10
print(rectangle.height)

rectangle.height = 24
print(rectangle.height)

```