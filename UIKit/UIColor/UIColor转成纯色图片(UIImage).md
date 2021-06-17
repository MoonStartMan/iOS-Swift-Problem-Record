# UIColor转成纯色图片(UIImage)

通过扩展 extension 来给UIColor添加方法

``` swift

extension UIColor {
	
	func asImage(_ size: CGSize) -> UIImage ? {
		var resultImage: UIImage? = nil
		let rect = CGRect(x: 0, y: 0, width: size.width, height: size.height)
		UIGraphicsBeginImageContextWithOptions(rect.size, false, UIScreen.main.scale)
		gurad let context = UIGraphicsGetCurrentContext() else {
			return resultImage
		}
		
		context.setFillColor(self.cgColor)
		context.fill(rect)
		resultImage = UIGraphicsGetImageFromCurrentImageContext()
		UIGraphicsEndImageContext()
	}
}

```

使用

``` swift

let colorImage = UIColor.black.asImage(CGSize(width: 100, height: 100));

```