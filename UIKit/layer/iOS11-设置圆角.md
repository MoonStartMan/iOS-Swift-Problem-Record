# iOS11-设置圆角

## 新增属性

iOS11对圆角功能进行了改善，layer新增了maskedCorners属性：

``` objective-C

@property CACornerMask maskedCorners
CA_AVAIABLE_STARTING (10.13, 11.0, 11.0, 4.0);

```

## 结构体类型

``` objective-C

typedef NS_OPTIONS (NSUInteger, CACornerMask)
{
	kCALayerMinXMinYCorner = 1U << 0,	//	左上
	kCALayerMaxXMinYCorner = 1U << 1,	//	右上
	kCALayerMinXMaxYCorner = 1U << 2, //	左下
	kCALayerMaxXMaxYCorner = 1u << 3,	//	右下
}

```

## 实例代码

``` swift

view.layer.maskedCorners = [.layerMaxXMaxYCorner,.layerMinXMaxYCorner]

```

## 圆角同时也支持动画

``` swift

UIViewPropertyAnimator.init(duration: 1.0, curve: .linear) {
	view3.layer.cornerRadius = 0
}.startAnimation()

```