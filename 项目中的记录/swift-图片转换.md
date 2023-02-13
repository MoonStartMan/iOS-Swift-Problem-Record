# swift-图片转换

## 转换图片为二进制流的形式

``` swift

func saveImageData(image: UIImage) -> Data? {
  if let cgImage = image.cgImage {
    let saveImage = UIImage(cgImage: cgImage, scale: image.scale, orientation: imageOrientation)
    let imageData = try? NSKeyedArchiver.archivedData(withRootObject: saveImage, requiringSecureCoding: false)
    return imageData
  }
  return nil
}

```

## 转化二进制流为图片形式

``` swift

func getImage(imageData: Data) -> UIImage? {
  if let image = try? NSKeyedUnarchiver.unarchivedObject(ofClass: UIImage.self, from: imageData) {
  	return image
  }
  return nil
}

```