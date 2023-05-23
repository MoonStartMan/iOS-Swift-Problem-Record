# iOS-录屏、截屏判断

## 录屏检测

``` swift

//	录屏
NotificationCenter.default.addObserver(self, selector: #selector(screensCaptured), name: UIScreen.capturedDidChangeNotification, object: nil)
        NotificationCenter.default.addObserver(self, selector: #selector(becomeActive), name: UIApplication.didBecomeActiveNotification, object: nil)
        
        
deinit {
	NotificationCenter.default.removeObserver(self, name: UIApplication.userDidTakeScreenshotNotification, object: nil)
}

```

## 屏幕是否在录制中

``` swift

UIScreen.main.isCaptured

```