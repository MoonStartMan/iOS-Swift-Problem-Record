# swift-UILabel设置行高和字间距

## 设置行间距

``` swift

///	设置间距
let style = MSMutableParagraphStyle()
/// 间隙
style.lineSpacing = 5
label.attributedText = NSAttributedString(string: text, attributes: [NSAttributedString.Key.paragraphStyle: style])

```

## 设置字间距

### 关键词NSAttributedString.Key.kern

``` swift

label.attributedText = NSAttributedString(string: "洒洒", attributes: [NSAttributedString.Key.kern : 5])

```