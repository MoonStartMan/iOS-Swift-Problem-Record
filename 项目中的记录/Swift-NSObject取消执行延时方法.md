# Swift-NSObject取消执行延时方法

``` swift

func autoDismiss() {
    NSObject.cancelPreviousPerformRequests(withTarget: self)
    perform(#selector(dismissView), with: nil, afterDelay: 0.5)
}
    
@objc func dismissView() {
    self.removeFromSuperview()
    self.dismiss()
}

```