# UIStackView

UIStackView是iOS中的一个视图容器,用于在水平或垂直方向上排列其子视图。它提供了一种简单的方式来组织和布局视图，无需手动计算和设置视图的位置和尺寸。

## UIStackView中常用的属性

| 属性 | 用途 |  |
| :-: | --- | --- |
| axis | 确定 UIStackView 的布局方向，可以是水平（.horizontal）或垂直（.vertical） | |
| alignment | 决定 UIStackView 内部子视图在交叉轴上的对齐方式，可以是顶部对齐（.top）、居中对齐（.center）、底部对齐（.bottom）等 | |
| distribution | 决定 `UIStackView` 内部子视图在主轴上的分布方式，可以是均匀分布（`.fillEqually`）、根据内容大小自适应分布（`.fillProportionally`）等 | |
| spacing | 确定 `UIStackView` 内部子视图之间的间距大小 | |
| arrangedSubviews | 用于添加和管理 `UIStackView` 中的子视图 | |

### UIStackView的distribution属性

| 属性 | 说明 | |
| :-: | --- | --- |
| fill | 子视图将填充整个 `UIStackView` 的主轴空间，子视图的尺寸会被拉伸或压缩以填充剩余空间。这是默认的分布方式 | |
| fillEqually | 子视图将平均分配 `UIStackView` 的主轴空间，每个子视图的尺寸相等 | |
| fillProportionally | 子视图将根据其内容的大小自适应地分配 `UIStackView` 的主轴空间。内容较大的子视图将获得更多的空间，而内容较小的子视图将获得较少的空间 | |
| equalSpacing | 子视图之间的间距相等，但子视图的尺寸不会被调整 | |
| equalCentering | 子视图之间的间距相等，并且每个子视图相对于 `UIStackView` 的中心对齐 | |

## 代码实例

``` swift

class ViewController: UIViewController {
    
    private var coverStackView: UIStackView = UIStackView()
    
    private var leftStackView: UIStackView = UIStackView()
    
    private var rightStackView: UIStackView = UIStackView()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        setupView()
    }

    private func setupView() {
        coverStackView.translatesAutoresizingMaskIntoConstraints = false
        coverStackView.distribution = .fill
        coverStackView.axis = .horizontal
        coverStackView.alignment = .center
        coverStackView.spacing = 100
        
        view.addSubview(coverStackView)
        coverStackView.snp.makeConstraints { make in
            make.centerX.equalToSuperview()
            make.centerY.equalToSuperview()
        }
        
        coverStackView.addArrangedSubview(leftStackView)
        coverStackView.addArrangedSubview(rightStackView)
        
        leftStackView.translatesAutoresizingMaskIntoConstraints = false
        leftStackView.distribution = .fillEqually
        leftStackView.axis = .vertical
        leftStackView.alignment = .center
        leftStackView.spacing = 20
        
        // 添加标签和按钮
        let label1 = UILabel()
        label1.text = "Label 1"
        leftStackView.addArrangedSubview(label1)
        
        let button1 = UIButton(type: .system)
        button1.setTitle("Button 1", for: .normal)
        leftStackView.addArrangedSubview(button1)
        
        let label2 = UILabel()
        label2.text = "Label 2"
        leftStackView.addArrangedSubview(label2)
        
        let button2 = UIButton(type: .system)
        button2.setTitle("Button 2", for: .normal)
        leftStackView.addArrangedSubview(button2)
        
        let label3 = UILabel()
        label3.text = "Label 3"
        leftStackView.addArrangedSubview(label3)
        
        let button3 = UIButton(type: .system)
        button3.setTitle("Button 3", for: .normal)
        leftStackView.addArrangedSubview(button3)
        
        rightStackView.translatesAutoresizingMaskIntoConstraints = false
        rightStackView.distribution = .fillEqually
        rightStackView.axis = .vertical
        rightStackView.alignment = .center
        rightStackView.spacing = 20
        
        // 添加标签和按钮
        let label4 = UILabel()
        label4.text = "Label 4"
        rightStackView.addArrangedSubview(label4)
        
        let button4 = UIButton(type: .system)
        button4.setTitle("Button 4", for: .normal)
        rightStackView.addArrangedSubview(button4)
        
        let label5 = UILabel()
        label5.text = "Label 5"
        rightStackView.addArrangedSubview(label5)
        
        let button5 = UIButton(type: .system)
        button5.setTitle("Button 5", for: .normal)
        rightStackView.addArrangedSubview(button5)
        
        let label6 = UILabel()
        label6.text = "Label 6"
        rightStackView.addArrangedSubview(label6)
        
        let button6 = UIButton(type: .system)
        button6.setTitle("Button 6", for: .normal)
        rightStackView.addArrangedSubview(button6)
    }
}

```