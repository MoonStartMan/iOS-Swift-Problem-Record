# Swift-单例的三种写法

## 类常量class constant(建议使用方式)

``` swift

class Singleton {
	static let sharedInstance = Singleton()
}

```

## 嵌套结构体变量格式

``` swift

class Singleton {
	class var sharedInstance: Singleton {
		struct Static {
			static let instance: Singleton = Singleton()
		}
		return Static.instance
	}
}

```

## 类似OC的创建方式(dispatch_once)(最不建议)

``` swift

class Singleton {
	class var sharedInstance: Singleton {
		struct Static {
			static var onceToken: dispatch_once_t = 0
			static var instance: Singleton? = nil
		}
		dispatch_once(&Static.onceToken) {
			Static.instance = Singleton()
		}
		return Static.instance!
	}
}

```