# UIScrollView-停止滑动的回调

## UIScrollView有三个Bool类型属性

1. isTracking
2. isDragging
3. isDecelerating

在3种动作触发的(DidEndDecelerating, DidEndDragging)两个方法中, isTracking、isDragging、isDecelerating的Bool值分别为：

## 停止类型1：

### DidEndDecelerating: 

isTracking: 0, isDragging: 0, isDecelerating: 0

## 停止类型2：

### DidEndDragging: 

isTracking: 1, isDragging: 0, isDecelerating: 1

### DidEndDecelerating:

isTracking: 0, isDragging:0, isDecelerating: 0

## 停止类型3

### DidEndDragging:

isTracking: 1, isDragging: 0, isDecelerating: 0

## 代码实现

``` swift

func scrollViewDidEndDragging(_ scrollView: UIScrollView, willDecelerate decelerate: Bool) {
  let dragToDragStop = scrollView.isTracking && !scrollView.isDragging && !scrollView.isDecelerating
  if dragToDragStop {
  	scrollViewDidEndScroll(scrollView: scrollView)
  }
}

func scrollViewDidEndDecelerating(_ scrollView: UIScrollView) {
  let scrollToScollStop = !scrollView.isTracking && !scrollView.isDragging && !scrollView.isDecelerating
  if scrollToScollStop {
  	scrollViewDidEndScroll(scrollView: scrollView)
  }
}

```