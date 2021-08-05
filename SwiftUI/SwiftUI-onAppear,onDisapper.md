# SwiftUI-onAppear,onDisapper

+ SwiftUI里面的```onAppear()```等价于UIKit里面的```ViewDidAppear()```
+ SwiftUI里面的```onDisappear()```等价于UIKit里面的```ViewDidDisappear()```

``` swift

var body: some View {
        
        NavigationView{
            List {
                ForEach (0 ..< 10, id: \.self) { index in
                    Text("\(index)")
                }
            }
        }
        .onAppear() {
            print("onAppear")
        }
        .onDisappear() {
            print("onDisappear")
        }
    }

```