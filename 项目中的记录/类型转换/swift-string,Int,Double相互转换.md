# swift-string,Int,Double相互转换

``` swift

var str = "Hello, playground"
//	1 字符串转Int Double Float
var str1 = "818"
//	转Int
var val1 = Int(str1);
//	转Double
var val2 = Double(str1);
//	转Float
var val3 = Float(str1);

//	如果25.0 转Int，则需要先转为Double类型再将其转换为Int类型

var val4 = "25.0"
let count = Double(val4);
let varl_int = Int(count);

print(val3!);

```

## 数字转换为字符串

``` swift

var num1 = 25;
var str2 = "\(num1)";
//	如果是Int类型的话 直接进行转
var str3 = String(num1);

//	如果是Double类型的话 可以通过以下方式进行转换
var str4 = String(stringInterpolationSegment: num1);

```

## 数字相互转换

``` swift

var num2 = 25.0;
//	Double 转为 Int
var num3 = Int(num2);

```