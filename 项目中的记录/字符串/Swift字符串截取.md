# Swift字符串截取

每一个String值都有一个关联的索引(index)类型, String.Index, 它对应着字符串中的每一个 Character的值。

使用**startIndex**获取String的第一个Character的索引。

使用**endIndex**获取String的最后一个Character的索引。

使用String的**index(before: )**或**index(after:)**,可以立即得到前面或者后面的一个索引。

通过**index(_:offsetBy:)**获取对应偏移量的索引


``` swift

let welcome = "hello world"

print(welcome[welcome.startIndex])
// h
print(welcome[welcome.index(after: welcome.startIndex)])
// e
print(welcome[welcome.index(before: welcome.endIndex)])
// d
let someIndex = welcome.index(welcome.startIndex, offsetBy: 3)
print(welcome[someIndex])
// l
let anotherIndex = welcome.index(welcome.endIndex, offsetBy: -3)
print(welcome[anotherIndex])
// r

```

