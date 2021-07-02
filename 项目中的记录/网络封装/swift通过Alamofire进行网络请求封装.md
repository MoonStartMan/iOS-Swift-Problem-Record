# swift通过Alamofire进行网络请求封装

## 通过cocopods安装Alamofire

1. ``` pod init ```
2. ``` vim podfile ```
3. 在编辑面板输入安装版本
``` vim
# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

target 'NewToday' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for NewToday
        pod 'Alamofire', '4.8.2'
end
```

这里我安装的版本为: 4.8.2

4. ``` pod install ```

## 新建HttpDates.swift进行封装

``` swift

import Foundation

import Alamofire    //  网络请求

private let httpShareInstance = HttpDatas()

//  数据请求方法
enum MothodType {
    case get
    case post
}

class HttpDatas: NSObject {
    
    //  单例
    class var shareInstance: HttpDatas {
        return httpShareInstance
    }
}

extension HttpDatas
{
    
    /// 网络请求通用版
    /// - Parameters:
    ///   - type: 数据请求方式 get/post
    ///   - URLString: 请求数据的路径
    ///   - paramaters: 请求数据需要的参数
    ///   - finishCallBack: 请求成功后通过这个block把数据回调
    func requestDatas(_ type: MothodType, URLString: String, paramaters: [String: Any]?, finishCallBack: @escaping (_ response: Any) -> ()) {
        
        //  获取请求类型
        let method = type == .get ? HTTPMethod.get : HTTPMethod.post
        
        //  发送网络请求
        Alamofire.request(URLString, method: method, parameters: paramaters, encoding: URLEncoding.default, headers: nil).responseJSON {
            (responseJson) in
            //  判断请求是否成功
            guard responseJson.result.value != nil else {
                print(responseJson.result.error)
                return
            }
            
            //  获取结果
            guard responseJson.result.isSuccess else {
                return
            }
            
            //  成功就把请求的数据回调回去
            if let value = responseJson.result.value {
                finishCallBack(value)
            }
        }
    }
}

```