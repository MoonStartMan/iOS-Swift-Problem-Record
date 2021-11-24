# UILabel计算宽高、添加删除线

## 计算宽度/高度

``` swift

///	方法一：已具有label，给定宽度限制，计算 label 的高度
let size = label.sizeThatFits(CGSizeMake(limitW, CGFloat(MAXFLOAT)))

///	方法二：已知字符串和字号(+1)，通过 NSString 的 sizeWithAttributes 方法计算
let priceStr = NSString.init(format:"¥ %@",goodsModel.price_disct)
let attributes = [NSFontAttributeName:UIFont.systemFontOfSize(14)]
let size = priceStr.sizeWithAttributes(attributes)

///	方法三：已知字符串，字号(+1)和宽度限制，通过 NSStirng 的 boundingRectWithSize 方法计算
let priceStr = NSString.init(format:"¥ %@",goodsModel.price_disct)
let attributes = [NSFontAttributeName:UIFont.systemFontOfSize(14)]
let size = priceStr.boundingRectWithSize(CGSizeMake(CGFloat(MAXFLOAT), 30), options: .UsesLineFragmentOrigin, attributes: attributes, context: nil).size

```

## 添加删除线

``` swift

let textStr = NSAttributedString(string: priceStr, attributes: [NSAttributedString.Key.strikethroughStyle: NSUnderlineStyle.single.rawValue])
textLabel.attributedText = textStr

```

## Demo地址

[Demo](https://github.com/MoonStartMan/Swift-iOS-Demo/tree/master/Text-Demo)

