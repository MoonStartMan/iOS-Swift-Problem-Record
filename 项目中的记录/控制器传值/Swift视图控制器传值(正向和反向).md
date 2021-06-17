# Swift视图控制器传值(正向和反向)

## 视图控制器间正向传值

正向传值有两种方式：第一种是通过属性传值，第二种是通过构造方法传值

### 通过属性传值

``` swift

let vc = ViewController()
vc.data = "通过data属性传值"
self.present(vc, animated: true, completion: nil)

```

### 通过构造方法传值

``` swift

//	在ViewController控制器中实现构造方法如下
init(data: String) {
	self.data = data
	super.init(nibName:nil, bundle: nil)
}

//	在要调用的地方调用ViewController控制器的构造方法实现数据传递
let vc = ViewController(data: "通过构造方法传值")
self.present(vc, animated: true, completion: nil)

```

## 视图控制器间反向传值

### 通过协议实现反向传值

``` swift

//	在控制器VC_2中声明协议以及协议方法
protocol ViewControllerProtocol {
	func sentData(data: String)
}

//	控制器VC_2
class ViewController: UIViewController {
//	声明一个Optional类型的代理属性
	var delegate: ViewControllerProtocol?
}

//	在控制器VC_2需要反向传值的地方调用该方法进行协议传值,会在VC_1中的sentData方法中接受到此值
delegate?.sentData(data:"反向传值")

//	在控制器VC_1中遵守协议
class homeVC: UIViewController, ViewControllerProtocol

//	在控制器VC_1中需要跳转到VC_2的地方制定代理
let vc = ViewController()
vc.delegate = self
self.present(vc, animated: true, completion: nil)

//	在VC_1中实现协议方法
func sentData(data: String) {
	//	data	即为VC_1反向传递过来的值
}

```