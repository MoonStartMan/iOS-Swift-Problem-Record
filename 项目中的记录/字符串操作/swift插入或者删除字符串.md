# swift插入或者删除字符串

## 插入字符串

``` swift

var str = "ABC"
str.inset("D", at: str.index(str.startIndex, offsetBy:1))
print("\(str)")

//	结果
//	ADBC

```

## 删除指定字符串

``` swift

var str = "ABC"
str.remove(at: str.startIndex)
print("\(str)")

//	结果
//	BC

```