# swift-判断客户端是否安装QQ并发起会话

``` swift

private func goToQQGroup() {
	let urlString = self.getQQGroupUrl()
	if let url = URL(string: urlString) {
		if UIApplication.shared.canOpenURL(url) {
			UIApplication.shared.openURL(inApp: url)
		} else {
      let popWindowView = MSAlertPopWindowView()
      popWindowView.title = "未检测到QQ应用,已复制群号".localized()
      popWindowView.iconImage = UIImage(named: "common_alert_confirm")
      popWindowView.show()
      UIPasteboard.general.string = "\(self.QQGroup)"
		}
	}
}

```