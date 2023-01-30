# swift-读取plist文件

``` swift

///	读取
var tipsDataDictionary: [String: Any] {
	guard let categoryListPath = Bundle.main.url(forResource: "data", withExtension: "plist") else {
	print("找不到plist")
	return [:]
	}
	do {
		let listData = try Data(contentsOf: categoryListPath)
		do {
			let listDictionary = try PropertyListSerialization.propertyList(from: listData, options: [], format: nil) as! [String: Any]
			return listDictionary
		} catch {
			fatalError("plist数据转换失败")
		}
	} catch {
		fatalError("文件路径不存在")
	}
	return [:]
}

```