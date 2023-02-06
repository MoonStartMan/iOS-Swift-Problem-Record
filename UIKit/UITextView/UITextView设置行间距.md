# UITextView设置行间距


``` swift

let paragraphStyle = NSMutableParagraphStyle()
paragraphStyle.lineSpacing = 5.0
paragraphStyle.alignment = .left

let attributes = [NSAttributedString.Key.paragraphStyle: paragraphStyle]
textView.typingAttributes = attributes

```