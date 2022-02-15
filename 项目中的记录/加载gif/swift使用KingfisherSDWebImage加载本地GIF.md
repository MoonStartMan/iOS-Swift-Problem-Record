# swift使用Kingfisher/SDWebImage加载本地GIF

## SDWebImage方法

``` swift

  let imageView =UIImageView(frame: CGRect(x:0, y:0, width: BGVIEW_WIDTH, height: BGVIEW_WIDTH))

imageView.image=UIImage.sd_animatedGIF(with: gifDataas!Data)

```

## Kingfisher方法

``` swift

let path =Bundle.main.path(forResource:"loading", ofType:"gif")

        let image =UIImageView(frame: CGRect(x:0, y:0, width: BGVIEW_WIDTH, height: BGVIEW_WIDTH))

        image.kf.setImage(with:ImageResource(downloadURL:URL(fileURLWithPath: path!)))

```