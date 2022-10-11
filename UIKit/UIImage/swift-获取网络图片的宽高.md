# swift-获取网络图片的宽高

``` swift

/// 网络图片宽度
let imageWidth: CGFloat = image.size.width
/// 网络图片高度
let imageHeight: CGFloat = image.size.height
/// 获取当前的图片的固定宽度: 屏幕宽度减去左右两侧边距,再算出高度
let currentHeaerWidth: CGFloat = kScreenW - (kMargin * 2)
let currentHeaderHeight: CGFloat = currentHeaerWidth * imageHeight / imageWidth
let oldHeaderHeight: CGFloat = kHeaderSize.height
let newHeaderHeight: CGFloat = oldHeaderHeight + currentHeaderHeight

```