# swift-键盘相关操作

## 键盘显示与收起

### 键盘显示

``` swift

NotificationCenter.default.addObserver(self, selector: #selector(handleKeyboardWillShow(notification:)), name: UIResponder.keyboardWillShowNotification, object: nil)

@objc func handleKeyboardWillShow(notification: NSNotification) {
    //  得到键盘frame
		if let userInfo: NSDictionary = notification.userInfo as NSDictionary? {
			let value = userInfo.object(forKey: MSColorValueView.keyboardFrameEndUserInfoKey)
			let keyboardRec = (value as AnyObject).cgRectValue
			let height = keyboardRec?.size.height ?? 0
			keyboardShowBack?(height)
    }
}

```

### 键盘收起

``` swift

NotificationCenter.default.addObserver(self, selector: #selector(handleKeyboardWillHide(notification:)), name: UIResponder.keyboardWillHideNotification, object: nil)

@objc func handleKeyboardWillHide(notification: NSNotification) {
    keyboardHideBack?()
}

```

## 键盘输入限制输入长度

``` swift

func textField(_ textField: UITextField, shouldChangeCharactersIn range: NSRange, replacementString string: String) -> Bool {
//  限制只能输入带#的7位数
if let text = textField.text {
	let newText = (text as NSString).replacingCharacters(in: range, with: string)
	if newText.count > 7 {
		return false
	}
	let result = isHexColor(newText)
		if result {
			let color = UIColor.hex(newText)
			currentColor = color
			colorValueBack?(color)
		}
	}
	return true
}

```

## 键盘收起/离开焦点判断

``` swift

/// 键盘收起 输入框判断
func textFieldDidEndEditing(_ textField: UITextField, reason: UITextField.DidEndEditingReason) {
	let text = textField.text
	let expression = "^#([0-9a-fA-F]{6})$"
	let regx = try? NSRegularExpression.init(pattern: expression, options: .caseInsensitive)
	if let results = regx?.matches(in: text ?? "", options: [], range: NSRange(location: 0, length: text?.count ?? 0)) {
		if results.count == 0 {
			MSPopUp.showHint(msg: "请填写正确的色值", onView: nil, mask: false,
			maskColor: nil, backgroundColor: nil, atYOffset: 0,
			showAnimationTime: 0.3, stayTime: 1, hideAnimationTime: 0.3)
		}
	}
}

```

## 键盘收起

``` swift

/// 键盘收起
func textFieldShouldReturn(_ textField: UITextField) -> Bool {
	textField.resignFirstResponder()
	keyboardHideBack?()
	return true
}

```

## 移除监听

``` swift

deinit {
	/// 移除监听
	NotificationCenter.default.removeObserver(self)
}

```