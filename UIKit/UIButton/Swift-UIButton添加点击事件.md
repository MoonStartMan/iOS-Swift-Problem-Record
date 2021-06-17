# Swift-UIButton添加点击事件

``` Swift

override func viewDidLoad() {
	super.viewDidLoad()
	//	创建按钮 按钮类型为自定义
	let button = UIButton.init(type: .custom)
	//	将按钮添加到视图中
	view.addSubview(button)
	button.backgroundColor = .red
	button.frame = CGRect.init(x: 100, y: 100, width: 200, height: 30)
	button.tag = 1
	//	添加点击方式，不区分传参与不传参
	button.addTarget(self, action: #selector(tapped), for: .touchUpInside)
}

//	按钮点击事件
@objc func tapped(sender: UIButton) {
	print(sender.tap)
}

```