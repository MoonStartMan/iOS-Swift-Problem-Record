# swift从UIColor中读取RGBA数据

给UIColor增加扩展

``` swift

extension UIColor {
	var rgba: (red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat) {
	var red: CGFloat = 0
	var green: CGFloat = 0
	var blue: CGFloat = 0
	var alpha: CGFloat = 0
	getRed(&red, green: &green, blue: &blue, alpha: &alpha)
	return (red, green, blue, alpha)
	}
}

```