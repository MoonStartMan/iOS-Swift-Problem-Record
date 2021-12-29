# swift-将字符串拆分成数组(把一个字符串分割成字符串数组)

## 使用componentsSeparatedByString()方法

### 实例代码

``` swift

let str = "北京、上海、深圳、香港"
print ("原始字符串:\(str)")

let splitedArray = str.componentsSeparatedByString("、")
print("拆分后的数组：\(splitedArray)")

```

### 执行结果


```

原始字符串: 北京、上海、深圳、香港
拆分后的数组: ["北京"、"上海"、"深圳"、"香港"]

```

## 使用characters.split()方法

### 实例代码

``` swift

let str = "北京、上海、深圳、香港"
print("原始字符串：\(str)")
 
let splitedArray = str.characters.split{$0 == "、"}.map(String.init)
print("拆分后的数组：\(splitedArray)")

```

### 执行结果

```

原始字符串: 北京、上海、深圳、香港
拆分后的数组: ["北京"、"上海"、"深圳"、"香港"]

```