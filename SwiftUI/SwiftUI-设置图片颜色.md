# SwiftUI-设置图片颜色


## renderingMode

— renderingMode参数:swifttui渲染图像的模式。
— 返回:修改后的' ' Image ' '。

``` public func renderingMode(_ renderingMode: Image.TemplateRenderingMode?) -> Image ```

``` swift

public enum TemplateRenderingMode {

	/// A mode that renders all non-transparent pixels as the foreground
	/// color.
	/// 一种将所有非透明像素呈现为前景的模式
	///	颜色。
	case template
	/// A mode that renders pixels of bitmap images as-is.
	///
	/// For system images created from the SF Symbol set, multicolor symbols
	/// respect the current foreground and accent colors.
	/// 按原样渲染位图图像像素的模式。
	/// 对于从SF Symbol集合创建的系统图像，多颜色符号
	/// 尊重当前前景并强调颜色。
	case original

```

## 核心代码

``` swift

Image("setting_right_bar_icon")
.renderingMode(.template)

```

## 完整代码

``` swift

Image("setting_right_bar_icon")
.resizable()
.renderingMode(.template)
.foregroundColor(Color.init("Black-White"))
.scaledToFit()
.frame(width: 24, height: 24)
.padding(.trailing, 16)

```