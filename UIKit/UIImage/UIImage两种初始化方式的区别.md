# UIImage两种初始化方式的区别

``` swift

UIImage(named: String)
UIImage(named: String, in: Bundle?, with: UIImage.Configuration?)

```

## imageNamed

imageNamed的优点是当加载时会缓存图片。这个方法用一个指定的名字在系统缓存中查找如果这个缓存图片存在的话便返回图。如果缓存中没有找到相应的图片，这个方法从指定的文档中加载然后缓存并返回这个对象。

## imageWithContentOfFile

imageWithContentsOfFile仅加载图片，不进行缓存处理。

