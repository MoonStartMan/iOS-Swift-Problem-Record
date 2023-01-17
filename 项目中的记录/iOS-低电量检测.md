# iOS-低电量检测

## 定义获取进程信息的ProcessInfo

``` swift

private let kProcessInfo = ProcessInfo()

```

## 根据进程信息检测低电量模式

``` swift

///	低电量检测

func checkAndMonitorPowerMode() {
  if kProcessInfo.isLowPowerModeEnabled {
    ///	低电量模式需要做的事情
  }
}

///	低电量模式监听方法

NotificationCenter.default.addObserver(self, 
selector: #selector(didChangePowerMode(notification:)),
name: Notification.Name.NSProcessInfoPowerStateDidChange,
object: nil)

@objc func didChangePowerMode(notification: Notification) {
  if kProcessInfo.isLowPowerModeEnabled {
  	///	低电量模式所需要做的事情
  }
}


```