# 获取collectionView当前点击item的frame和point

## 获取frame

``` swift

let attributes = collectionView.layoutAttributesForItem(at: indexPath)
guard let attributesPoint = attributes?.frame else {
	return
}

```

## 获取center

``` swift

let attributes = collectionView.layoutAttributesForItem(at: indexPath)
guard let attributesPoint = attributes?.center else {
	return
}

```