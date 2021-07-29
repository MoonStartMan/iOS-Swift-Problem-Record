# SwiftUI-设置Text上下左右间隔

top,leading,bottom,trailing

``` swift

.padding(EdgeInsets(top: 16, leading: 10, bottom: 0, trailing: 5))

```

完整代码

``` swift

Text("请输入6-16位密码")
                        .foregroundColor(hexColor(hex: 0xFF0000))
                        .font(.caption2)
                        .fontWeight(.medium)
                        .padding(EdgeInsets(top: 10, leading: 10, bottom: 0, trailing: 0))

```