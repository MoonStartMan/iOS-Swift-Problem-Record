# swift-BlurView设置高斯模糊(毛玻璃)

## 设置白色模糊毛玻璃效果

关键代码

``` swift

let blurEffect = UIBlurEffect(style: .systemMaterialLight)
visualEffectView = UIVisualEffectView(effect: blurEffect)
addSubview(visualEffectView)
visualEffectView.snp.makeConstraints { make in
	make.bottom.left.right.equalToSuperview()
	make.height.equalTo((32 + kSafeAreaBottom).fitH())
}
visualEffectView.layer.masksToBounds = true

```