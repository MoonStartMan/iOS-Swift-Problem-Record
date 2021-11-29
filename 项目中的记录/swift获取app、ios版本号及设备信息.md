# swift获取app、ios版本号及设备信息

``` swift

func versionCheck(){
    let infoDictionary = NSBundle.mainBundle().infoDictionary
    let appDisplayName:AnyObject? = infoDictionary["CFBundleDisplayName"] //程序名称
    let majorVersion :AnyObject? = infoDictionary ["CFBundleShortVersionString"]//主程序版本号
    let minorVersion :AnyObject? = infoDictionary ["CFBundleVersion"]//版本号（内部标示）
   //设备信息
    let iosVersion : NSString = UIDevice.currentDevice().systemVersion //ios版本
    let identifierNumber = UIDevice.currentDevice().identifierForVendor //设备udid
    let systemName = UIDevice.currentDevice().systemName //设备名称
    let model = UIDevice.currentDevice().model //设备型号
    let localizedModel = UIDevice.currentDevice().localizedModel //设备区域化型号如A1533

    let appVersion = majorVersion as! String
    print(appVersion)
}

```