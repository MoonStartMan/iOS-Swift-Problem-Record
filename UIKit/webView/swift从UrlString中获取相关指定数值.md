# swift从wkWebView中获取相关指定数值

## 获取url

``` swift

guard let url = navigationAction.request.url else { return }

```

## 获取scheme

``` swift

let components = URLComponents(url: url, resolvingAgainstBaseURL: false)
print("\(components?.scheme)") // https 或者 http

```

## 获取pathExtension

``` swift

let postfnx = url.pathExtension
//	这里我获取的是图片路径
print("\(postfnx)") // "jpg"或"jpeg"或"png"

```