# iOS-CAReplicatorLayer

## 使用解释

CAReplicatorLayer用于创建 layer 的指定数量副本，副本间有不同的几何坐标、显示属性（delay、transform）和颜色等。

## 参数说明

+ instanceCount: 要创建的副本数，包括原始Layer。默认值是1，即不创建副本。
+ instanceDelay: 指定副本显示延时。默认值为0.0秒,即同步显示。
+ instanceTransform: 向前一个副本添加transform，得到当前副本。默认为CATransform3DIdentity。
+ preservesDepth: 是否将子图层展平到平面中。默认为false。如果为true，则CAReplicatorLayer表现与CATransformLayer相似，同时受CATransformLayer同样限制。
+ instanceColor: 指定原始图层的颜色。默认为不透明白色。
+ instanceRedOffset: 指定颜色红色通道偏移量。向k-1实例添加偏移，得到k实例颜色。默认为0.0.
instanceGreenOffset、instanceBlueOffset、instanceAlphaOffset与instanceRedOffset类似，只是通道不同。

## 代码使用

``` swift

var replicatorLayer = CAReplicatorLayer()
replicatorLayer.bounds = CGRect(x: 0, y: 0, width: bounds.size.width, height: bounds.size.height)
layer.addSublayer(replicatorLayer)

replicatorLayer.instanceCount = 10

var transform = CATransform3DIdentity
transform = CATransform3DTranslate(transform, 0, 50, 0)
transform = CATransform3DRotate(transform, .pi / 5.0, 0, 0, 1)
transform = CATransform3DTranslate(transform, 0, -50, 0)
replicatorLayer.instanceTransform = transform

replicatorLayer.instanceBlueOffset = -0.1
replicatorLayer.instanceGreenOffset = -0.1

let layer = CALayer()
layer.bounds = CGRect(x: 0, y: 0, width: 25, height: 25)
layer.position = layer.position
layer.backgroundColor = UIColor.white.cgColor

replicatorLayer.addSublayer(layer)

```