# swift-协议泛型associatedtype

定义一个协议时,有的时候声明一个或多个关联作为协议定义的一部分将会非常有用。
关联类型为协议中的某个类型提供了一个占位名(或者说别名)，其代表的实际类型在协议被采纳时才会被指定。
你可以通过associatedtype关键字来指定关联类型。
比如使用协议声明更新cell的方法:

``` swift

//	模型
struct Model {
	let age: Int
}

//	协议,使用关联类型
protocol TableViewCell {
	associatedType T
	func updateCell(_ data: T)
}

//	遵守TableViewCell
class MyTableViewCell: UITableViewCell, TableViewCell {
	typealias T = Model
	func updateCell (_ data: Model) {
		//	do something ...
	}
}

```
