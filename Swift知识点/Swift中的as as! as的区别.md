# Swift中的as as! as?的区别

## as:类型一致或者子类

仅当一个值的类型在运行时(runtime)和as模式右边的指定类型一致 - 或者是该类型的子类 - 的情况下，才会匹配这个值。如果匹配成功，被匹配的值的类型被转换成as模式左边指定的模式。

``` swift

class Animal{}
class Dog: Animal {}

let d = Dog()
d as Animal

```

## as!父类强转子类

``` swift

class Animal {}
class Dog: Animal {}

let a: Animal = Dog{}
a as! Dog

```

不加!编译会报错

## as?转换失败返回nil

``` swift

class Animal {}
class Dog: Animal {}
class Cat: Animal {}

let animal: Animal = Cat()
animal as! Dog
animal as? Dog

```

animal as! Dog 编译会报错 as?就是对的