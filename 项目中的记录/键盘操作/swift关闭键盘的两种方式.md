# swift关闭键盘的两种方式

## 方法一

对单个的UITextField调用resignFirstResponder方法,使其失去第一响应者。

``` swift

sender.resignFirstResponder()

```

## 方法二

对UIViewController，重写touchesBegan，并调用endEditing方法

``` swift

override func touchesBegan(touches: Set<UITouch>, withEvent event: UIEvent?) {
	view.endEditing(true)
}

```