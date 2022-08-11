# UITextField-焦点事件

## 进入焦点事件

``` swift

func textFieldDidBeginEditing(_ textField: UITextField) {
	//	do something
}

```

## 离开焦点事件

``` swift

func textFieldDidEndEditing(_ textField: UITextField) {
	//	do something
}

```

都需要遵循UITextFieldDelegate协议。