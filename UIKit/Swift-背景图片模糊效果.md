# Swift-背景图片模糊效果

``` swift

var blurEffect =UIBlurEffect(style:UIBlurEffectStyle.Dark)
var blurEffectView =UIVisualEffectView(effect: blurEffect)
blurEffectView.frame=view.bounds
backgroundImageView.addSubview(blurEffectView)

```