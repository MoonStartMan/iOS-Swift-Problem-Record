# swift - 调起邮件发送

## 1. 导入头文件

``` swift

import MessageUI //	导入头文件

```


## 2. 添加代理

``` swift

MFMailComposeViewControllerDelegate

```

## 3. 相关调用

``` swift

if MFMailComposeViewController.canSendMail() {	//	是否可以发邮件	//	如果不能,去系统设置接收邮箱
	let mailView = MFMailComposeViewController()
	mailView.mailComposeDelegate = self
	mailView.setToRecipients(["********@gmail.com"])//	接收邮件的邮箱
	mailView.setSubject("邮件标题")
	mailView.setMessageBody("文件内容", isHTML: false)
	self.present(mailView, animated: false, completion: nil)
} else if let emailUrl = createEmailUrl(to: recipientEmail, subject: subject, body: body) {
	UIApplication.shared.open(emailUrl)
}

 private func createEmailUrl(to: String, subject: String, body: String) -> URL? {
	let subjectEncoded = subject.addingPercentEncoding(withAllowedCharacters: .urlHostAllowed)!
	let bodyEncoded = body.addingPercentEncoding(withAllowedCharacters: .urlHostAllowed)!
	let gmailUrl = URL(string: "googlegmail://co?to=\(to)&subject=\(subjectEncoded)&body=\(bodyEncoded)")
	let outlookUrl = URL(string: "ms-outlook://compose?to=\(to)&subject=\(subjectEncoded)")
	let yahooMail = URL(string: "ymail://mail/compose?to=\(to)&subject=\(subjectEncoded)&body=\(bodyEncoded)")
	let sparkUrl = URL(string: "readdle-spark://compose?recipient=\(to)&subject=\(subjectEncoded)&body=\(bodyEncoded)")
	let defaultUrl = URL(string: "mailto:\(to)?subject=\(subjectEncoded)&body=\(bodyEncoded)")
	if let gmailUrl = gmailUrl, UIApplication.shared.canOpenURL(gmailUrl) {
		return gmailUrl
	} else if let outlookUrl = outlookUrl, UIApplication.shared.canOpenURL(outlookUrl) {
		return outlookUrl
	} else if let yahooMail = yahooMail,UIApplication.shared.canOpenURL(yahooMail) {
		return yahooMail
	} else if let sparkUrl = sparkUrl, UIApplication.shared.canOpenURL(sparkUrl) {
	return sparkUrl
	}
	return defaultUrl
}

```

## 4. 在info.plist文件添加以下代码

``` info.plist

<key>LSApplicationQueriesSchemes</key>
<array>
    <string>googlegmail</string>
    <string>ms-outlook</string>
    <string>readdle-spark</string>
    <string>ymail</string>
</array>

```