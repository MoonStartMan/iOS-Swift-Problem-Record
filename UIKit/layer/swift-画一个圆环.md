# swift-画一个圆环

``` swift

class MSEditColorControlView: UIView {

    private var centerView: UIView!
    /// 路径
    private var path: UIBezierPath!
    /// 圆环
    private var trackLayer: CAShapeLayer!

    override init(frame: CGRect) {
        super.init(frame: frame)
        
        setupUI()
    }
    
    private func setupUI() {
        centerView = UIView()
        addSubview(centerView)
        centerView.snp.makeConstraints { make in
            make.center.equalToSuperview()
            make.width.height.equalTo(8)
        }
        centerView.layer.borderWidth = 2
        centerView.layer.cornerRadius = 4
        centerView.layer.masksToBounds = true
        
        trackLayer = CAShapeLayer()
        layer.addSublayer(trackLayer)
    }
    
    private func drawLayer() {
        path = UIBezierPath(arcCenter: CGPoint(x: bounds.midY, y: bounds.midY), radius: bounds.size.width / 2, startAngle: 0, endAngle: 360, clockwise: true)
        trackLayer.frame = bounds
        trackLayer.fillColor = UIColor.clear.cgColor
        trackLayer.lineWidth = 12
        trackLayer.path = path.cgPath
    }
    
    override func layoutSubviews() {
        super.layoutSubviews()
        drawLayer()
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    func updateColor(color: UIColor) {
        centerView.layer.borderColor = color.cgColor
        trackLayer.strokeColor = color.cgColor
    }

}


```