# Swift-从应用中跳转到AppStore页面并打分

## 1. 弹窗消息框

``` swift

//弹出消息框
        let alertController = UIAlertController(title: "觉得好用的话，给我个评价吧！",
                                                message: nil, preferredStyle: .alert)
        let cancelAction = UIAlertAction(title: "暂不评价", style: .cancel, handler: nil)
        let okAction = UIAlertAction(title: "好的", style: .default,
                                     handler: {
                                        action in
                                        self.gotoAppStore()
        })
        alertController.addAction(cancelAction)
        alertController.addAction(okAction)
        self.present(alertController, animated: true, completion: nil)

```

## 2.跳转到应用的Appstore页面

``` swift

func gotoAppStore() {
        let urlString = "应用商店的APPID"
        if let url = URL(string: urlString) {
            //根据iOS系统版本，分别处理
            if #available(iOS 10, *) {
                UIApplication.shared.open(url, options: [:],
                                          completionHandler: {
                                            (success) in
                })
            } else {
                UIApplication.shared.openURL(url)
            }
        }
    }

```