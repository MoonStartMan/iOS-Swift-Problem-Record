# 在SwiftUI中使用UIView以及UIViewController

## 在SwiftUI中使用UIViewController

### 使用UIviewcontroller步骤

+ 遵循UIViewControllerRepresentable并实现其中两个方法

``` swift

struct DraftsView: UIViewControllerRepresentable {
    //	这里写你要使用UIKit来完成的UIViewController，我这里是DraftsViewController
    typealias UIViewControllerType = DraftsViewController
    //	这里修改返回值，返回你的UIViewController，我这里是DraftsViewController
    func makeUIViewController(context: Context) -> DraftsViewController {
        let draftVC = DraftsViewController()
        return draftVC
    }
    
    func updateUIViewController(_ uiViewController: UIViewControllerType, context: Context) {
        
    }
}

```

+ 在SwiftUI文件中使用

``` swift

HStack {
	DraftsView()
	Text("123")
}

```

## 在SwiftUI中使用UIView

### 使用UIView步骤

遵循UIViewRepresentable并实现其中两个方法，与上面类似

``` swift

struct DraftsView: UIViewControllerRepresentable {
    //	这里写你要使用UIKit来完成的UIView，我这里是DraftsView
    typealias UIViewType = DraftsView
    //	这里修改返回值，返回你的UIView，我这里是DraftsView
    func makeUIViewController(context: Context) -> DraftsView {
        let draftView = DraftsView()
        return draftView
    }
    
    func updateUIViewController(_ uiViewController: UIViewControllerType, context: Context) {
        
    }
}

```

