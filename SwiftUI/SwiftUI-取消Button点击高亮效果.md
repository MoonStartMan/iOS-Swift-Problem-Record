# SwiftUI-取消Button点击高亮效果

## 核心代码

创建一个不突出显示的自定义ButtonStyle

``` swift

struct StaticButtonStyle: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
    }
}

```

## 调用及Demo

``` swift

Button(action: {
	//	需要执行的点击事件
}, label: {
	Text("点击按钮")
})
//	调用
.buttonStyle(StaticButtonStyle())

```