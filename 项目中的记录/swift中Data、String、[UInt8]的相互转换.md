# swift中Data、String、[UInt8]的相互转换


``` swift

var data = Data()
var array = [UInt8]()
var str = ""

//	Data[UInt8]
data.append(10)
array = [UInt8](data)
print(array)//[10]

//  [UInt8]转Data
array = [1, 2, 3, 4, 5]
data = Data(array)
print(data.count)//	5

//	Data转String
data.removeAll()
data.append(contentsOf: [0x31, 0x32, 0x33])
str = String(data: data, encoding: .utf8)!
print(str)

//	String转Data
str = "world"
data = str.data(using: .utf8)!
print(data.count) //5

//	String转[UInt8]
str = "hello"
array = [UInt8](str.utf8)
print(array) // [104, 101, 108, 108, 111]

//	[UInt8]转String
array = [0x39, 0x39, 0x39]
str = String(bytes: array, encoding: .utf8)!
print(str) // 999

```