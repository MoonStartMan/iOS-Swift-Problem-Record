# swift-WKWebView与JavaScript的简单交互

## 创建WKWebView

+ 导入WebKit框架, 在控制器中添加WKWebView
+ 遵循WKScriptMessageHandler
+ 配置WKUserContentController

``` swift

let config = WKWebViewConfiguration()
let wkUController = WKUserContentController()
///	这里的name是与前端约定好的方法名称
wkUController.add(self, name: "reportEvent")
config.userContentController = wkUController
let preferences = WKPreferences()
preferences.javaScriptEnabled = true
preferences.javaScriptCanOpenWindowsAutomatically = true
config.preferences = preferences
webView = WKWebView(frame: .zero, configuration: config)
view.addsubView(webView)

```

## 实现WKScriptMessageHandler协议里的方法

``` swift

extension MSWebViewController: WKScriptMessageHandler {
	func userContentController(_ userContentController: WKUserContentController, didReceive message: WKScriptMessage) {
		if message.name == "reportEvent" {
			if let msg = message.body as? NSString {
				///	执行方法
			}
		}
	}
}

```

## 网页端的JS方法

``` JavaScript

function jsUseWKWebView() {
	window.webkit.messageHandlers.reportEvent.postMessage("js传给webView的数据")
}

```

## 原生调用网页JS的方法

```  swift

let jsStr = "webViewUseJs('\(传给js的参数)')"
self.webView?.evaluateJavaScript(jsStr, completionHandler: { result, error in
	print("###\(String(describing: result))###\(String(describing: error))")
})

```

## 移除ScriptMessageHandler

``` swift

deinit {
	self.webView?.configuration.userContentController.removeScriptMessageHandler(forName: "submit")
}

```