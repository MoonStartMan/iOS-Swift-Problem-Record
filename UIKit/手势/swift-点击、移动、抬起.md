# swift-点击、移动、抬起

具体方法

1、通知调用者当有一个或者多个手指触摸到了视图或者窗口时触发此方法。
touches是UITouch的集合，通过UITouch我们可以检测触摸事件的属性，是单拍还是双拍，还有触摸的位置等。

``` swift

func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?)

```

2、告诉接收者一个或者多个手指在视图或者窗口上触发移动事件。
默认不允许多点触摸。如果要接收多点触摸事件必须将UIView的属性设置为true。

``` swift

func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?)

```

3、当一个触摸事件结束时发出的UITouch实例对象。

``` swift

func touchesEnded(_ touches: Set<UITouch>, with event: UIEvent?)

```

4、通知接收者当系统发出取消事件的时候（如低内存消耗的告警框)

``` swift

func touchesCancelled(_ touches: Set<UITouch>, with event: UIEvent?)

```

