# swift-UIScrollView整页滚动获取当前索引

我这里UIScrollView是整页滚动

``` swift

var scrollBack: ((_ index: Int) -> Void)?

func scrollViewDidEndDecelerating(_ scrollView: UIScrollView) {
  let x: CGFloat = scrollView.contentOffset.x
  let scrollW: CGFloat = scrollView.frame.size.width
  let index: Int = (Int)((x + scrollW / 2) / scrollW)
  scrollBack?(index)
}

```