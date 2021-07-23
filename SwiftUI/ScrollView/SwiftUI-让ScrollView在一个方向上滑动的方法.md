# SwiftUI-让ScrollView在一个方向上滑动的方法

将ScrollView放到GeometryReader里面去，就会在一个方向上滑动了。

``` swift

GeometryReader { geometry in
                ScrollView(.horizontal, showsIndicators: false) {
                    HStack(alignment: .top, spacing: 0) {
                        ForEach(self.items) { landmark in
                            CategoryItem(landmark: landmark)
                        }
                    }
                }
                .frame(height: 185)
            }

```