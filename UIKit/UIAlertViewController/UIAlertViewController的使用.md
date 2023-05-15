# UIAlertViewController的使用

## 弹窗类型

+ Alert
+ AlertSheet

## 按钮样式

+ Default: 蓝色
+ Cancel: 蓝色加粗
+ Destructive: 红色(警告)

## 绑定按钮点击事件

+ 默认情况下,即我们设置按钮处理事件为nil,当我们点击会使AlertView消失掉

例如：

``` swift

alertContr.addAction(UIAlertAction(title:"", style: .Default, handler: nil))

```

+ 自定义事件绑定，有两种方式：1.绑定定义好的方法，2.使用闭包。代码举例，为方便起见，我们使用一种特殊闭包，官方称之为TrailingClosure

``` swift

alertContr.addAction(UIAlertAction(title: "取消", style: .Cancel) {
	clickHandler in /*\**do what you want*/
})

```

## 高级使用

Swift提供了更加高级的用法，我们不仅可以往UIAlertView上添加按钮，我们还可以添加TextField

``` swift

func loginAction() {
	let alertContr = UIAlertController(title: "标题", message: "Swift弹窗框", preferredStyle: .Alert)
	alertContr.addTextFieldWithConfigurationHandler {
		(textField: UITextField!) -> Void in
		textField.placeholder = "登录"
	}
	alertContr.addTextFieldWithConfigurationHandler {
		(textField: UITextField!) -> Void in
		textField.placeholder = "密码"
		textField.secureTextEntry = true
	}
	alertContr.addAction(UIAlertAction(title: "确定", style: .Default) {
		clickHandler in
		let loginName = alertContr.textFields!.first! as UITextField
		let password = alertContr.textFields!.last! as UITextField
		NSLog("LoginName: \(loginName.text!), Password: \(password.text!)")
	})
	alertContr.addAction(UIAlertAction(title: "取消", style: .Cancel) {
		clickHandler in
		NSLog("点击了取消")
	})
	self.presentViewController(alertContr, animated: true, completion: nil)
}

```