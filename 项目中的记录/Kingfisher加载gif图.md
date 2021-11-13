# Kingfisher加载gif图

## Kingfisher加载本地资源

``` swift

let path = Bundle.main.path(forResource: "123", ofType: "gif")
let url = URL(fileURLWithPath: path!)
let provider = LocalFileImageDataProvider(fileURL: url)
imageView.kf.setImage(with: provider)

```

## 加载网络资源

``` swift

if let url = URL(string: model?.imageUrl ?? "") {
                imageView.kf.setImage(with: url)
}

```

## 加载网络资源并带有占位图

``` swift

if let url = URL(string: model?.imageUrl ?? "") {
                imageView.kf.setImage(with: url, placeholder: UIImage(named: "list_normal_img"))
            }

```