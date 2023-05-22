# swift-系统StoreKit应用内跳转APP Store和评分

## 导入系统StoreKit的头文件

``` swift

import StoreKit

```

## 应用内评分

应用内评分主要使用SKStoreReviewController，只需要一个方法，UI也是非常的简洁美观。

1. iOS10.3之后支持
2. Apple限制开发者一年最多只能向用户调用3次评分UI

``` swift

SKStoreReviewController.requestReview()

```

3. 兼容方式写法

``` swift

func lg_iTunesScoreComment(appId: String) {
  if #available(iOS 10.3 , *) {
  	SKStoreReviewController.requestReview()
  } else {
    let openStr = "itms-apps://itunes.apple.com/app/id\(appId)?action=write-review"
    if UIApplication.shared.canOpenURL(URL(string: openStr)) {
      if #available(iOS 10.0, *) {
      UIApplication.shared.open(URL(string: openStr), options: [], completionHandler: nil)
    } else {
      UIApplication.shared.canOpenURL(URL(string: openStr))
    }
    } else {
      print("无法打开链接")
    }
  }
}

```

## 应用内跳转App Store

使用应用内跳转主要是 present SKStoreProductViewController

1. 创建和设置 Parameters

``` swift

import UIKit
import StoreKit

class LGStoreProduct: NSObject {
    
    static let share = LGStoreProduct()
    private override init() { super.init()}
    private var parentVc:UIViewController?
    
    func lg_openStore(currentVc: UIViewController, appID: String)  {
        parentVc = currentVc
        currentVc.present(self.storeVc, animated: true, completion: nil)
        storeVc.loadProduct(withParameters: [SKStoreProductParameterITunesItemIdentifier: appID], completionBlock: {
            (result, error) in
            if result && error == nil {
                print("链接加载成功！！！")

            } else {
                print(error as Any)
            }
        })
    }
    
    
    lazy var storeVc: SKStoreProductViewController = {
        let storeVc = SKStoreProductViewController()
        storeVc.delegate = self
        return storeVc
    }()
}

```

2. SKStoreProductViewControllerDelegate方法，设置dissmiss回调

``` swift

extension LGStoreProduct: SKStoreProductViewControllerDelegate {
// Sent if the user requests that the page be dismissed
  func productViewControllerDidFinish(_ viewController: SKStoreProductViewController) {
		parentVc?.dismiss(animated: true, completion: nil)
	}
}

```