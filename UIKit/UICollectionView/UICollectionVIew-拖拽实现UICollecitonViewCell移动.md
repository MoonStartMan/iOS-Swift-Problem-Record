# UICollectionVIew-拖拽实现UICollecitonViewCell移动

## 给CollectionView添加拖拽手势

``` swift

let longPress = UILongPressGestureRecognizer(target: self, action: #selector(longPressMoving(longPress:)))
collectionView.addGestureRecognizer(longPress)

```

## 实现拖拽方法

``` swift

@objc func longPressMoving(longPress: UILongPressGestureRecognizer) {
  switch longPress.state {
  case .began:
    //这里是上报的当前Cell的IndexPath
    //手势作用的位置
    let point = longPress.location(in: self.collectionView)
    let selectIndexPath = self.collectionView?.indexPathForItem(at: point)
    //找到当前的cell
    let selectCell = self.collectionView?.cellForItem(at: selectIndexPath!)
    //拽起变大动画效果
    UIView.animate(withDuration: 0.2) {
    	selectCell?.transform = CGAffineTransform(scaleX: 1.1, y: 1.1)
    }
  	//开始移动
  	self.collectionView?.beginInteractiveMovementForItem(at: selectIndexPath!)
  case .changed:
    //这里上报的是当前触摸点的位置
    	let point = longPress.location(in: self.collectionView)
    //更新移动的位置
    	self.collectionView?.updateInteractiveMovementTargetPosition(point)
  case .ended:
    //结束移动
    	self.collectionView?.endInteractiveMovement()
  default:
    //移动失败或者取消
    //选中状态清除
    	self.collectionView?.cancelInteractiveMovement()
    }
  }

```

## 实现UICollectionView协议

``` swift

func collectionView(_ collectionView: UICollectionView, moveItemAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath) {
  let sourceData = dataArray[sourceIndexPath.item]
  self.dataArray.remove(at: sourceIndexPath.item)
  self.dataArray.insert(sourceData, at: destinationIndexPath.item)
  collectionView.reloadData()
}

```