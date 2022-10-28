# swift-设置文字过渡渐变色

``` swift

let textLayer: CATextLayer = CATextLayer()
textLayer.string = "Hello, World!"
textLayer.font = UIFont.systemFont(ofSize: 14.0, weight: .bold)
textLayer.fontSize = 14.0
let animation = CABasicAnimation(keyPath: "foregroundColor")
animation.fromValue = UIColor.hex("#1A1A1A").cgColor
animation.toValue = UIColor.hex("#FFFFFF").cgColor
animation.repeatCount = 1
animation.isRemovedOnCompletion = false
animation.fillMode = .forwards
animation.duration = 0.3

```