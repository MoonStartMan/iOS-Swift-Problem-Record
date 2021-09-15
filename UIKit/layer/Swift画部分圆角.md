# Swift画部分圆角

## 画左上及右上的圆角

``` swift

let maskPath = UIBezierPath(roundedRect: self.bounds, byRoundingCorners: [UIRectCorner.topLeft, UIRectCorner.topRight], cornerRadii: CGSize(width: 20, height: 20))
let maskLayer = CAShapeLayer()
maskLayer.frame = self.bounds
maskLayer.path = maskPath.cgPath
self.layer.mask = maskLayer

```