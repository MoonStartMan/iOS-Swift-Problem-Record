# Swift-关键字typealias

## 使用Typeealias的目的

使用typealias的主要目的是使我们的代码更清晰并易于阅读。

## 创建类型别名

Typealias使用关键字typealias声明：

``` swift

typealias name = existing type

```

Swift可以帮助你对大多数类型使用typealias

+ 内置类型(例如: 字符串,整数)
+ 用户定义的类型(例如: 类,结构,枚举)
+ 复杂类型(例如: 闭包)

## 内置类型的Typealias

Typealias可用于所有内置数据类型,例如String, Int, Float等。

### 例如

``` swift

typealias EmloyeeName = String

```

在这里,我们已将EmployeeName声明为String的类型别名。因此，我们可以稍后使用它而不是String类型。

### 例如
如果不使用Typealias, 则声明为：

``` swift
let name:String = "Alex"
```
通过创建Typealias EmployeeName, 我们可以编写与上述相同的声明：

``` swift
let name:EmployeeName = "Alex"
```
你可以看到两个示例都创建了相同的常量类型字符串, 但是后面的示例对于人类来说更容易理解。

## 用户定义类型的类型别名

在Swift中, 你可以创建自己的数据类型。假设你必须创建一个数据类型Employee, 所以可以使用一个类来创建它：

``` swift

class Employee {

}

```

现在,你可以按以下方式在数组中创建一组雇员:

``` swift

var employees: Array<Employee> = []

```

在这里，你可以使用Typealias为数组创建自己的类型,以使代码更具可读性:

``` swift

typealias Employees = Array<Employee>

```

现在,声明看起来像:

``` swift

var employees: Employees = []

```

在你的代码中很容易理解。