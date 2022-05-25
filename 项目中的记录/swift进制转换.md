# swift进制转换

## 十进制转二进制

``` swift

String(15, radix: 2) ///	返回"1111"

```

## 二进制转十进制

``` swift

func binary2dec(num: String) -> Int {
	var sum = 0
	for c in num.charaters {
		sum = sum * 2 + Int("\(c)")
	}
	return sum
}

binary2dec("1111")	返回15

```

## 十进制转十六进制

``` swift

String(15, radix: 16)

```

## 十六进制转十进制

``` swift

extension String {
	static func changeToInt(num: String) -> Int {
		let str = num.uppercaseString
		var sum = 0
		for i in str.uft8 {
			sum = sum * 16 + Int(i) - 48
			if i >= 65 {
				sum -= 7
			}
		}
		return sum
	}
}
String.changeToInt(number2)

```

``` swift

func changeToInt(num: String) -> Int {
	let str = num.uppercaseString
	var sum = 0
	for i in str.utf8 {
		sum = sum * 16 + Int(i) - 48
		if i >= 65 {
			sum -= 7
		}
	}
	return sum
}
changeToInt("f")

```