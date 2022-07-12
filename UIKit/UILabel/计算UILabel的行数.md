# 计算UILabel的行数

``` swift

func getHeightByWidth(label: UILabel, width: CGFloat) -> Int {
	let labelHeight = label.sizeThatFits(CGSize(width: width, height: CGFloat(MAXFLOAT))).height
	let count = labelHeight / label.font.lineHeight
	return Int(count)
}

```