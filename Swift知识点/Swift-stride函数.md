# swift-stride函数

## from to

``` swift

//	最后一个值小于to的值
for index in stride(from: 0, to: 12, by: 3) {
	print(index)
}
//	print 0, 3, 6, 9

```

``` swift

//	最后一个值大于to的值
for index in stride(from: 12, to: 0, by: -3) {
	print(index)
}
//	print 12, 9, 6, 3

```

## from through

``` swift

//	最后一个值小于等于through的值
for index in stride(from: 0, through: 12, by: 3) {
	print(index)
}
//	print 0, 3, 6, 9, 12

```

``` swift

//	最后一个值大于through的值
for index in stride(from: 12, through: 0, by: -3) {
	print(index)
}
//	print 12, 9, 6, 3, 0

```

## 数组操作

``` swift

let array = Array(1...31)
let arr = stride(from: 0, array.count, by: 7).map { (index) -> [Int] in
	if (index + 7) > array.count {
		return Array(array[index...])
	} else {
		return Array(array[index ..< index+7] )
	}
}
print(arr)
//[[1, 2, 3, 4, 5, 6, 7], [8, 9, 10, 11, 12, 13, 14], [15, 16, 17, 18, 19, 20, 21], [22, 23, 24, 25, 26, 27, 28], [29, 30, 31]]
```


``` swift
let array = Array(1...31)
let arr = stride(from: 0, through: array.count, by: 7).map { (index) -> [Int] in
	if (index + 7) > array.count {
		return Array(array[index...])
	} else {
		return Array(array[index ..< index + 7])
	}
}
print(arr)
//	[[1, 2, 3, 4, 5, 6, 7], [8, 9, 10, 11, 12, 13, 14], [15, 16, 17, 18, 19, 20, 21], [22, 23, 24, 25, 26, 27, 28], [29, 30, 31]]

```

``` swift

let array = Array(1...31)
let step = 7
let arr = stride(from: 0, to: array.count - (array.count % step), by: step).map {
	Array(array[$0..<$0+step])
}
print(arr)
//	[[1, 2, 3, 4, 5, 6, 7], [8, 9, 10, 11, 12, 13, 14], [15, 16, 17, 18, 19, 20, 21], [22, 23, 24, 25, 26, 27, 28]

```