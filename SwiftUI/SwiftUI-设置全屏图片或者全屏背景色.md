# SwiftUI-设置全屏图片或者全屏背景色

## 关键代码

``` swift

.resizable()
.scaledToFill()
.edgesIgnoringSafeArea(.all)

```

## 设置全屏图片

``` swift

.background(
	Image("bg")
		.resizable()
		.scaledToFill()
		.edgesIgnoringSafeArea(.all)
)

```

## 设置全屏颜色

``` swift

.background(
	Color(red: 0 / 255.0, green: 0 / 255.0, blue: 0 / 255.0, opacity: 1.0)
		.resizable()
		.scaledToFill()
		.edgesIgnoringSafeArea(.all)
)

```