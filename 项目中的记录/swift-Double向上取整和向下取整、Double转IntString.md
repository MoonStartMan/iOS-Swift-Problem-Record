# swift-Double向上取整和向下取整、Double转Int/String

``` swift

extension Double {

	func intValue() -> Int {
		return Int(self)
	}
	
	func stringIntValue() -> String {
		return String(Int(self))
	}
	
	func stringValue() -> String {
		return String(self)
	}
	
	func floorValue(bit: Int = 0) -> Double {
		var n = bit
		var s = 1.0
		while n > 0 {
			n -= 1
			s *= 10
		}
		return floor(self * s) / s
	}
	
	func floor2Value() -> Double {
		return floorValue(bit: 2)
	}
	
	func stringFloor2Value() -> String {
		return String(format: "%.2f", self.floor2Value())
	}
	
	func ceilValue(bit: Int = 0) -> Double {
		var n = bit
		var s = 1.0
		while n > 0 {
			n -= 1
			s *= 10
		}
		return ceil(self * s) / s
	}
	
	func ceil2Value() -> Double {
		return ceilValue(bit: 2)
	}
	
	func stringCeil2Value() -> String {
		return String(format: "%.2f", self.ceil2Value())
	}
	
}

```