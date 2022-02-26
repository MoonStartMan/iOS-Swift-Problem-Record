# 根据UIColor对象获取对应的RGBA值

``` swift

func getColorRGBA(color: UIColor) -> [CGFloat] {
	var red: CGFloat = 0.0
	var green: CGFloat = 0.0
	var blue: CGFloat = 0.0
	var alpha: CGFloat = 0.0
	color.getRed(&red, green: &green, blue: &blue, alpha: &alpha)
	return [red, green, blue, alpha]
}

```