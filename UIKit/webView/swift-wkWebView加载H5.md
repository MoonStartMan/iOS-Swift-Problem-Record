# swift-wkWebView返回上一级


``` swift

///	允许手势滑动
wkWebView.allowsBackForwardNavigationGestures = true

///	添加滑动手势
let swiperGesture = UISwipeGestureRecognizer(target: self, action: #selector(handleNavgationTransition(gap:)))
swiperGesture.delegate = self
view.addGestureRecognizer(swiperGesture)
navigationController?.interactivePopGestureRecognizer?.isEnabled = true
navigationController?.interactivePopGestureRecognizer?.delegate = self

///	返回上一页方法
 @objc func handleNavgationTransition(gap: UIGestureRecognizer) {
   if wkWebView.canGoBack {
   	wkWebView.goBack()
   } else {
   	MSLog.debug("不能返回")
   }
 }

```

