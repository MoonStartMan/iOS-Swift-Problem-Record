# swift数组遍历forEach、enumerated、iterator、indices

## forEach

1. 无法使用 break 或 continue 跳出或者跳过循环
2. 使用return 只能退出当前一次的循环体

``` swift

import UIKit
let numerArray = [0, 1, 2, 3, 4, 5, 6, 7]
numerArray.forEach { (num) in
	if num == 3 {
		return
	}
	print(num)
}

//	打印结果：0, 1, 2, 4, 5, 6, 7
```

## enumerated

通过enumerated()可以拿到索引

``` swift

import UIKit
let numerArray = [0, 1, 2, 3, 4, 5, 6, 7]
for (index, num) in numberArray.enumerated() {
	print("the index is :\(index)")
	print(num)
}

//	打印结果 the index is 0
//	0
//	打印结果 the index is 1
//	1
//	打印结果 the index is 2
//	2
//	打印结果 the index is 3
//	3
//	打印结果 the index is 4
//	4
//	打印结果 the index is 5
//	5
//	打印结果 the index is 6
//	6
//	打印结果 the index is 7
//	7

```

## 迭代器遍历

``` swift

import UIKit

let numerArray = [0, 1, 2, 3, 4, 5, 6, 7]
var numInerator = numberArray.makeIterator() 
while let num = numInerator.next() {
	print(num)
}
//	打印结果：0, 1, 2, 3, 4, 5, 6, 7

```

## 只获取索引

``` swift

import UIKit

let numerArray = [0, 1, 2, 3, 4, 5, 6, 7]
for i in numberArray.indices {
	print(numberArray[i])
}

//	打印结果: 0, 1, 2, 3, 4, 5, 6, 7

```