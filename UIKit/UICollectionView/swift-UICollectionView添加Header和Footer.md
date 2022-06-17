# swift-UICollectionView添加Header和Footer

## collectionView注册Header和Footer

``` swift

collectionView.register(SettingProfileView.self, forSupplementaryViewOfKind: UICollectionView.elementKindSectionHeader, withReuseIdentifier: headerID)
collectionView.register(SettingFooterView.self, forSupplementaryViewOfKind: UICollectionView.elementKindSectionFooter, withReuseIdentifier: footerID)

```

## 复用Header和Footer

``` swift

func collectionView(_ collectionView: UICollectionView, viewForSupplementaryElementOfKind kind: String, at indexPath: IndexPath) -> UICollectionReusableView {
  if kind == UICollectionView.elementKindSectionFooter {
    guard let footerView = collectionView.dequeueReusableSupplementaryView(
    ofKind: UICollectionView.elementKindSectionFooter,
    withReuseIdentifier: footerID,
    for: indexPath) as? SettingFooterView else {
      fatalError()
    }
    return footerView
	} else if kind == UICollectionView.elementKindSectionHeader {
      guard let headerView = collectionView.dequeueReusableSupplementaryView(
      ofKind: UICollectionView.elementKindSectionHeader,
      withReuseIdentifier: headerID,
      for: indexPath) as? SettingProfileView else {
      	fatalError()
      }
			return headerView
	}
	return UICollectionReusableView()
}

```
