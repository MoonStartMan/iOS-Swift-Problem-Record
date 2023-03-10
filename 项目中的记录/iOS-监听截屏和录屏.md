# iOS-监听截屏和录屏

## 截屏

### 监听

``` swift

NotificationCenter.default.addObserver(self, selector: #selector(screenshots), name: UIApplication.userDidTakeScreenshotNotification, object: nil)

@objc func screenshots() {
  let alertVC = UIAlertController(title: "提示", message: "你目前正在截屏", preferredStyle: .alert)
  let action = UIAlertAction(title: "知道了", style: .default) { action in
  	alertVC.dismiss(animated: true, completion: nil)
  }
  alertVC.addAction(action)
  present(alertVC, animated: true, completion: nil)
}

```

## 录屏

### 监听

``` swift

NotificationCenter.default.addObserver(self, selector: #selector(screenshots), name: UIScreen.capturedDidChangeNotification, object: nil)
  //  如果正在捕获此屏幕(例如,录制/空中播放/镜像等,则为真)
if UIScreen.main.isCaptured {
  screenshots()
}

@objc func screenshots() {
  let alertVC = UIAlertController(title: "提示", message: "你目前正在录屏", preferredStyle: .alert)
  let action = UIAlertAction(title: "知道了", style: .default) { action in
  	alertVC.dismiss(animated: true, completion: nil)
  }
  alertVC.addAction(action)
  present(alertVC, animated: true, completion: nil)
}

```