# 原型模式-Prototype-Pattern

原型模式是一种创建型设计模式，它允许我们通过复制现有对象来创建对象，而不是通过实例化类来创建。该模式主要用于创建复杂的对象，其中创建过程需要很大的开销或者涉及到与其他对象的交互。在iOS开发中，原型模式可以用于创建复杂的对象，例如视图控制器、视图或者数据模型等。通过复制现有对象，我们可以避免重新实例化对象和重新配置对象的属性，从而提高性能和减少代码重复。

## 实例代码

``` swift

// 定义一个可复制的原型协议
protocol Prototype: AnyObject {
	func clone() -> Self
}

// 实现原型协议的具体类
class ViewController: UIViewController, Prototype {
    var name: String
    
    init(name: String) {
        self.name = name
        super.init(nibName: nil, bundle: nil)
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    func clone() -> Self {
        return type(of: self).init(name: self.name)
    }
}

// 使用原型模式创建新对象
let originalViewController = ViewController(name: "Original")
let clonedViewController = originalViewController.clone()

print(originalViewController.name) // 输出: Original
print(clonedViewController.name) // 输出: Original

```