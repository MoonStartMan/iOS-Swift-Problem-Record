# swift给文字添加描边效果

## 封装方法

``` swift

/// 给字体添加描边效果 : strokeWidth为正数为空心文字描边 strokeWidth为负数为实心文字描边
private func drawOutlineAttributedString(
    string: String,
    fontSize: CGFloat,
    alignment: NSTextAlignment,
    textColor: UIColor,
    strokeWidth: CGFloat,
    widthColor: UIColor) -> NSAttributedString {
    let paragraph = NSMutableParagraphStyle()
    paragraph.alignment = alignment
    paragraph.lineHeightMultiple = 0.93
    let dic: [NSAttributedString.Key: Any] = [
        NSAttributedString.Key.font: UIFont.systemFont(ofSize: fontSize),
        NSAttributedString.Key.paragraphStyle: paragraph,
        NSAttributedString.Key.foregroundColor: textColor,
        NSAttributedString.Key.strokeWidth: strokeWidth,
        NSAttributedString.Key.strokeColor: widthColor,
        NSAttributedString.Key.kern: 1
    ]
    var attributedText: NSMutableAttributedString!
    attributedText = NSMutableAttributedString(string: string, attributes: dic)
    return attributedText
}

```