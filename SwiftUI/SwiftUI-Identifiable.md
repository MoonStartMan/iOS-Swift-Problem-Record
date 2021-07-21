# SwiftUI-Identifiable

## 作用

Identifiable非常简单实用，主要作用就是作为一个对象的唯一标识。

## Demo

### 没有使用Identifiable

``` swift

struct Expense {
    var id = UUID()
    var name: String
    var type: String
    var amount: Int
}

let expenses = [
    Expense(name: "房租", type: "房费开销", amount: 10),
    Expense(name: "吃饭", type: "日常开销", amount: 5),
    Expense(name: "唱歌", type: "娱乐开销", amount: 10),
]

ForEach(expenses, id: \.id) { item in
    Text(item.name)
}

```

### 使用Identifiable

``` swift

struct Expense: Identifiable {
    var id = UUID()
    var name: String
    var type: String
    var amount: Int
}

let expenses = [
    Expense(name: "房租", type: "房费开销", amount: 10),
    Expense(name: "吃饭", type: "日常开销", amount: 5),
    Expense(name: "唱歌", type: "娱乐开销", amount: 10),
]

ForEach(expenses) { item in
    Text(item.name)
}

```