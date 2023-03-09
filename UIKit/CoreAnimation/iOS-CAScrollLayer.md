# iOS-CAScrollLayer

这时可以使用CAScrollLayer, CAScrollLayer的scroll(to:)方法自动调整bounds的原点,使图层内容看起来是在滑动。

CoreAnimation不能识别用户手势，因此其不能将手势转换为滑动事件，另外也不会渲染滑动状态条和滑动弹性效果。

## 滚动实现方法

``` swift

layer.scroll(p: CGPoint)
layer.scrollRectToVisible(r: CGRect)

```


``` swift

class CAScrollLayerView: UIView {
    
    private var imageView: UIImageView = UIImageView()
    
    override class var layerClass: AnyClass {
        return CAScrollLayer.self
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        
        setup()
    }
    
    private func setup() {
        layer.masksToBounds = true
        backgroundColor = .lightGray
        
        let recognizer = UIPanGestureRecognizer(target: self, action: #selector(pan))
        addGestureRecognizer(recognizer)
        
        addSubview(imageView)
        imageView.snp.makeConstraints { make in
            make.edges.equalToSuperview()
        }
        imageView.image = UIImage(named: "scenery")
    }
    
    @objc func pan(_ recognizer: UIPanGestureRecognizer) {
        var offset = bounds.origin
        offset.x -= recognizer.translation(in: self).x
        offset.y -= recognizer.translation(in: self).y

        layer.scroll(offset)

        recognizer.setTranslation(CGPoint.zero, in: self)
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
}

```