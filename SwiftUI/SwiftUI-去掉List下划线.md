# SwiftUI-去掉List下划线

直接上码

``` swift

extension View {
    func listSeparatorNone(backgroundColor: Color = Color(.systemBackground)) -> some View {
        self.modifier(ListSeparatorNone(backgroundColor: backgroundColor))
    }
}

struct ListSeparatorNone: ViewModifier {

    var backgroundColor: Color = Color(.systemBackground)

    func body(content: Content) -> some View {
        content
            .listRowInsets(EdgeInsets(top: 0, leading: 0, bottom: 0, trailing: 0))
            .frame(maxWidth: .infinity, maxHeight: .infinity, alignment: .leading)
            .background(backgroundColor)
    }
}

```