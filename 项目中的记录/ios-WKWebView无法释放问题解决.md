# ios-WKWebView无法释放问题解决

## 造成原因

因为没有释放，导致无法走到deinit()方法里面

``` swift

let config = WKWebViewConfiguration()
let wkUController = WKUserContentController()
wkUController.add(self, name: "reportEvent")

```

通过以上代码，发现造成的原因为这个self引起的循环引用

## 解决办法

用一个其他对象来承载，打破循环。

``` swift

fileprivate class ScriptMessageHandler: NSObject, WKScriptMessageHandler {
	func userContentController(_ userContentController: WKUserContentController, didReceive message: WKScriptMessage) {
    if message.name == "reportEvent" {
			//	doSomething
    }
  }
}

```

解决后的代码

``` swift

let config = WKWebViewConfiguration()
let handler = ScriptMessageHandler()
wkUController.add(handler, name: "reportEvent")

```