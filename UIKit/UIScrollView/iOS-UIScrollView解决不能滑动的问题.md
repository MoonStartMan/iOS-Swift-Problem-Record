# iOS-UIScrollView与SnapKit解决不能滑动的问题以及不能显示的问题

## 错误用法

没有指定宽高，无法显示scrollView

``` swift

let scrollView = UIScrollView()
scrollView.delegate = self
scrollView.backgroundColor = .blue
view.addsubView(scrollView)
scrollView.snp.makeConstraints { (make) in
	make.edges.equalToSuperview()
}

let sonView = UIView()
scrollView.addSubview(sonView)
sonView.snp.makeConstraints { (make) in
	make.top.left.right.bottom.equalToSuperview()
}

```

这里会显示异常，导致UIScrollView的大小无法正常显示

## 正确用法

在UIScrollView里面放一个contentView,contentView与UIScrollView大小相等。

``` swift

scrollView = UIScrollView()
addSubview(scrollView)
scrollView.snp.makeConstraints { make in
    make.edges.equalToSuperview()
}
scrollView.showsHorizontalScrollIndicator = false
scrollView.showsVerticalScrollIndicator = false
scrollView.scrollsToTop = false
scrollView.contentSize = CGSize(width: 0, height: (kScreenH + kSafeAreaBottom + 56).fitH() )
scrollView.contentInsetAdjustmentBehavior = .never
scrollView.isScrollEnabled = true

///	添加ScrollContentView,设置起大小与scrollView的contentSize大小相等
scrollContentView.
scrollView.addSubview(scrollContentView)
scrollContentView.snp.makeConstraints { make in
  make.edges.equalToSuperview()
  make.width.equalTo(kScreenW)
  make.height.equalTo(kScreenH + 56.fitH())
}

```