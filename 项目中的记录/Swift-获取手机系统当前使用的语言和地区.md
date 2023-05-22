# Swift-获取手机系统当前使用的语言和地区

## 获取设备系统语言

``` swift

static func getCurrentLanguage() -> String {
	// 返回设备曾使用过的语言列表
    let languages: [String] = UserDefaults.standard.object(forKey: "AppleLanguages") as! [String]
    // 当前使用的语言排在第一
    let currentLanguage = languages.first
    return currentLanguage ?? "en-CN"
}

```


## 获取设备设置的地区

``` swift

/// 获取系统当前地区 en_CN/en_GB
static func getCurrentRegion() -> String {
    return NSLocale.current.identifier
}

```