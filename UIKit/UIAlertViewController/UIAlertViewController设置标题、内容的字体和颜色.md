# UIAlertViewController设置标题、内容的字体和颜色

## 设置标题和内容的字体

``` swift

func setLabelStyle(controller: UIAlertController, title: String, message: String) {
        let titleControllerStr = NSMutableAttributedString(string: title)
        titleControllerStr.addAttribute(.foregroundColor, value: UIColor.red, range: NSRange(location: 0, length: title.count))
        titleControllerStr.addAttribute(.font, value: UIFont.systemFont(ofSize: 18, weight: .bold), range: NSRange(location: 0, length: title.count))
        controller.setValue(titleControllerStr, forKey: "attributedTitle")
        
        let messageControllerStr = NSMutableAttributedString(string: message)
        messageControllerStr.addAttribute(.foregroundColor, value: UIColor.green, range: NSRange(location: 0, length: message.count))
        messageControllerStr.addAttribute(.font, value: UIFont.systemFont(ofSize: 12, weight: .semibold), range: NSRange(location: 0, length: message.count))
        controller.setValue(messageControllerStr, forKey: "attributedMessage")
    }

```

## 设置标题、内容的颜色

``` swift

func setActionColor(action: UIAlertAction, color: UIColor) {
        action.setValue(color, forKey: "titleTextColor")
    }

```