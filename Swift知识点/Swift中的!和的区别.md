# Swift中的!和?的区别

## ?和!的定义

?和!其实分别是Swift语言中对一种可选类型(Optional)操作的语法糖。

## 例子

``` Swift

var str1: String? = "Hello"
let greeting = "World!"
if (str1 != nil ) {
	let message = greeting + str!
	print(message)
}

```

其中 str1 是字符串类型的可选值。greeting 是肯定有值的。

所以要对str1用!进行拆包保证不会报错。(可选值+有值的会报错)