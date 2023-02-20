# UIViewAnimationWithBlock动画

## API

``` swift

UIView.animate(withDuration: <#T##TimeInterval#>, delay: <#T##TimeInterval#>, usingSpringWithDamping: <#T##CGFloat#>, initialSpringVelocity: <#T##CGFloat#>, animations: <#T##() -> Void#>)

```

## 参数解释

### usingSpringWithDamping

usingSpringWithDamping的范围为0.0f到1.0f，数值越小「弹簧」的振动效果越明显。

### initialSpringVelocity

initialSpringVelocity则表示初始的速度，数值越大一开始移动越快。

## 例子

``` swift

UIView.animate(withDuration: 0.3, delay: 0, usingSpringWithDamping: 0.5, initialSpringVelocity: 10, options: .curveEaseOut, animations: {
	// TODO
}, completion: nil)

```