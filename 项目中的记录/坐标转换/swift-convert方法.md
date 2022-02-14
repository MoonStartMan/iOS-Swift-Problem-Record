# swift-convert方法

## 1

作用: 坐标转换。将子级视图转换到父级视图，相对于父级视图的父视图位置。

``` swift

func convert(_ point: CGPoint, to coordinateSpace: UICoordinateSpace) -> CGPoint

open func convert(_ point: CGPoint, to view: UIView?) -> CGPoint

let tempPoint = CGPoint(x: 20, y: 20)
let result = toView.convert(tempPoint, to: fromView)

```

上面的函数式等价于

``` swift

let x = (toView.frame.origin.x + tempPoint.x - fromView.frame.origin.x)
let y = (toView.frame.origin.y + tempPoint.y - fromView.frame.origin.y)
let result = CGPoint(x: x, y: y)

```

## 2

``` swift

func convert(_ point: CGPoint, from coordinateSpace: UICoordinateSpace) -> CGPoint

open func convert(_ point: CGPoint, from view: UIView?) -> CGPoint

let tempPoint = CGPoint(x: 20, y: 20)
let result = toView.convert(tempPoint, from: fromView)

```

上面函数等价于

``` swift

let x = (fromView.frame.origin.x + tempPoint.x - toView.frame.origin.x)
let y = (fromView.frame.origin.y + tempPoint.y - toView.frame.origin.y)
let result = CGPoint(x: x, y: y)

```

## 3

``` swift

func convert(_ rect: CGRect, to coordinateSpace: UICoordinateSpace) -> CGRect
open func convert(_ rect: CGRect, to view: UIView?) -> CGRect
let tempRect = CGRect(x: 20, y: 20, width: 50, height: 50)
let result = toView.convert(tempRect, to: fromView)

```

上面的函数式等价于

``` swift

let x = (toView.frame.origin.x + tempRect.origin.x - fromView.frame.origin.x)
let y = (toView.frame.origin.y + tempRect.origin.y - fromView.frame.origin.y)
let width = tempRect.width
let height = tempRect.height
let result = CGRect(x: x, y: y, width: width, height: height)

```

## 4

``` swift

func convert(_ rect: CGRect, from coordinateSpace: UICoordinateSpace) -> CGRect

open func conver(_ rect: CGRect, from view: UIview) -> CGRect

let tempRect = CGRect(x: 20, y: 20, width: 50, height: 50)
let result = toView.convert(tempRect, from: fromView)

```

上面函数式等价于

``` swift

let x = (fromView.frame.origin.x + tempRect.origin.x - toView.frame.origin.x)
let y = (fromView.frame.origin.y + tempRect.origin.y - toView.frame.origin.y)
let width = tempRect.width
let height = tempRect.height
let result = CGRect(x: x, y: y, width: width, height: height)

```