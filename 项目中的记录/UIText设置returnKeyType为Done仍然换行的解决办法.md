# UIText设置returnKeyType为Done仍然换行的解决办法

设置文本字段的返回类型为Done后仍然换行没有收起键盘

``` swift

textView.returnKeyType = .done

```

解决办法

``` swift

func textView(_ textView: UITextView, shouldChangeTextIn range: NSRange, replacementText text: String) -> Bool {
  if text == "\n" {
  	textView.resignFirstResponder()
  }
	return true
}

```