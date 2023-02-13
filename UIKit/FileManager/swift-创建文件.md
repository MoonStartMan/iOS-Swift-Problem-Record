# swift-创建文件

``` swift

func createFileInDocuments(fileName: String) {
  let urlForDocument = fileManager.urls(for: .documentDirectory, in: .userDomainMask)
  let url = urlForDocument[0]
  let file = url.appending(path: fileName)
  let exist = fileManager.fileExists(atPath: file.path())
  if !exist {
  let createSuccess = fileManager.createFile(atPath: file.path(), contents: nil, attributes: nil)
  	print("文件创建结果: \(createSuccess)")
  }
}

```