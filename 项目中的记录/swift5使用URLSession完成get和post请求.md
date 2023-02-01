# swift5使用URLSession完成get和post请求

定义HTTP请求方式的枚举

``` swift

enum HTTPMethods: String {
	case post = "POST"
	case get = "GET"
}

```

实现请求

## GET请求

``` swift

class Request {
	
	static let request = Request()
	
	func getData<O>(url: String, method: HTTPMethods, dataType: O.Type, completion: @escaping (_ dataList: O) -> Void) where O: Decodable, O: Encodable {
		let session = URLSession(configuration: .default)
        
        if let url = URL(string: url) {
            var urlRequest = URLRequest(url: url)
            urlRequest.httpMethod = methond.rawValue
            let task = session.dataTask(with: urlRequest) { data, response, error in
                do {
                    let newData = String(data: data!, encoding: .utf8)?.data(using: .utf8)
                    let callbackData = try JSONDecoder().decode(dataType, from: newData!)
                    completion(callbackData)
                } catch {
                    print("请求失败")
                    return
                }
            }
            task.resume()
        }
	}
	
}

```

## POST请求

post请求与get请求大同小异 需要新增请求体

``` swift

urlRequest.setValue("application/x-www-form-urlencoded", forHTTPHeaderField: "Content-Type")
let postData = ["id": "xxxx", "name": "xxxx"]
let postString = postData.compactMap { (key, value) -> String in
	return "\(key)=\(value)"
}.joined(separator: "&")
urlRequest.httpBody = postString.data(using: .utf8)

```