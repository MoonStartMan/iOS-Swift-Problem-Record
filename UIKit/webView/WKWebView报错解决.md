# WKWebView报错解决

## 报错信息

``` error

Completion handler passed to -[WebWidgetVC webView:decidePolicyForNavigationAction:decisionHandler:] was not called

```

## 报错原因

因为 ``` decisionHandler ``` 被调用了两次。它只能被调用一次。

## 解决办法

``` swift

if navigationAction.targetFrame == nil {
    UIApplication.shared.open(url)
    decisionHandler(.cancel)
    return
} else {
    // =======> 第一次进入这里
    decisionHandler(.allow)
}

// 通过系统自带浏览器打开链接
UIApplication.shared.open(url)
// 取消decisionHandler，因为我们管理了navigationAction。
// =======> 第二次在这里
decisionHandler(.cancel)

```