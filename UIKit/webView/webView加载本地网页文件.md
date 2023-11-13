# webView加载本地网页文件

``` swift

///1. 获取本地H5的文件地址

let H5Path = ///	本地网页地址

///2. 如果查找到有本地的网页地址，则加载本地的网页地址并阻拦当前的跳转

decisionHandler(.cancel)

///	这里地址前面要添加"file://"
///	加载后需要return避免崩溃

if let localURL = URL(string: "file://" + indexHTMLPath) {
	webView.loadFileURL(localURL, allowingReadAccessTo: localURL.deletingLastPathComponent())
	return
}

```