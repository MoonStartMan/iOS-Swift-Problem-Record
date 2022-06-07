# swift-UILabel富文本设置


``` swift

let dic: [NSAttributedString.Key: Any] = [
    NSAttributedString.Key.font: UIFont.systemFont(ofSize: 12),
    NSAttributedString.Key.paragraphStyle: paragraph,
    NSAttributedString.Key.foregroundColor: textColor,
    NSAttributedString.Key.strokeWidth: strokeWidth,
    NSAttributedString.Key.strokeColor: widthColor,
    NSAttributedString.Key.kern: 1
]
var attributedText: NSMutableAttributedString!
attributedText = NSMutableAttributedString(string: string, attributes: dic)
return attributedText

```