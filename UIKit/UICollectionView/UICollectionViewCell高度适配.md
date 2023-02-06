# UICollectionViewCell高度适配

1. 设置CollectionView的自适应高度

``` swift

layout.estimatedItemSize = UICollectionViewFlowLayout.automaticSize

```

2. 在UICollectionViewCell中重写preferredLayoutAttributesFitting方法

``` swift

override func preferredLayoutAttributesFitting(_ layoutAttributes: UICollectionViewLayoutAttributes) -> UICollectionViewLayoutAttributes {
  setNeedsLayout()
  layoutIfNeeded()
  let attributes = super.preferredLayoutAttributesFitting(layoutAttributes)
  let height = contentLabel.frame.size.height
  var newFrame = attributes.frame
  newFrame.size.width = UIScreen.main.bounds.size.width
  newFrame.size.height = height + 20
  attributes.frame = newFrame
  return attributes
    }

```

注意：

必须要设置itemSize的预估大小 否则不生效。