# swift-根据图片URL保存到相册

``` swift

func downPic(url: URL) {
	if let data = NSData(contentsOf: url) as? Data,
           let image: UIImage = UIImage(data: data) {
            UIImageWriteToSavedPhotosAlbum(image, self, #selector(image(image: didFinishSavingWithError:contextInfo:)), nil)
        }
}

@objc func image(image: UIImage, didFinishSavingWithError: NSError?, contextInfo: AnyObject) {
        if didFinishSavingWithError != nil {
            MSPopUp.showHint("保存失败")
            return
        }
        MSPopUp.showHint("保存成功")
    }

```