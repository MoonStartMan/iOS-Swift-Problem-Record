# swift-通过URL地址打开web页面

** 通过UIApplication.shared.open()方法, 可以使用浏览器打开相应的网页。 **

``` swift

let urlString = "http://www.baidu.com"
	if let url = URL(string: urlString) {
		//	根据iOS系统版本，分别处理
		if #available(iOS 10, *) {
			UIApplication.shared.open(url, options: [:], completionHandler: { (success) in
			})
		} else {
			UIApplication.shared.openURL(url)
		}
	}

```