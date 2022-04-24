# swift-截取当前屏幕的图片

``` swift

func getcurrentMonitorImage() -> UIImage {
///	选择需要截取的区域View
        guard let monitorUnit = PTUnitManager.unit(for: MonitorUnit.self),
              let monitorview = monitorUnit.rtrUnit?.rtrPlayer.unityContainerView else {
            return UIImage()
        }
        ///	获取所在区域的大小
        let size = monitorview.frame.size
        UIGraphicsBeginImageContextWithOptions(size, false, UIScreen.main.scale)
        let rect = monitorview.bounds
        monitorview.drawHierarchy(in: rect, afterScreenUpdates: true)
        guard let snapshotImage = UIGraphicsGetImageFromCurrentImageContext() else {
            return UIImage()
        }
        UIGraphicsEndImageContext()
        return snapshotImage
    }

```