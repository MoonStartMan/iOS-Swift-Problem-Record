# UILabel-sizeToFit和sizeThatFits的使用区别

sizeToFit: 会计算出最优的size而且会改变自己的size
sizeThatFits: 会计算出最优的size但是不会改变自己的size

``` swift

label.sizeThatFits(size:	CGSize)

label.sizeToFit

```