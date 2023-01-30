# iOS-字典转JSON字符串

``` swift

extension Dictionary {
	func toJsonString() -> String? {
		guard let data = try? JSONSerialization.data(withJSONObject: self, options: .sortedKeys) else {
			return nil
		}
		guard let str = String(data: data, encoding: .uft8) else {
			return nil
		}
		return str
	}
}

```