# swift-ViewController返回上一级VC或者指定VC方法

## 返回上一级VC方法

``` swift

let lastVC = self.presentingViewController
lastVC?.dismiss(animated: true, completion: nil)

```

## 返回指定VC

``` swift

@objc func backController() {
let lastVC = self.presentingViewController
  if let VC = lastVC {
    if VC.isKind(of: ViewController.self) {
    	VC.dismiss(animated: true, completion: nil)
    }
  }
}


```