# Swift5-创建文件并存储到Documents

``` swift

class WXFileManager: NSObject {
    
    static let wxFileManager: WXFileManager = WXFileManager()
    
    let fileManager: FileManager = FileManager.default
    
    /// 创建文件
    func createFileInDocuments(fileName: String) {
        let urlForDocument = fileManager.urls(for: .documentDirectory, in: .userDomainMask)
        let url = urlForDocument[0]
        
        let file = url.appending(path: fileName)
        let exist = fileManager.fileExists(atPath: file.path())
        if !exist {
            let data = Data(base64Encoded: "aGVsbG8gd29ybGQ=", options: .ignoreUnknownCharacters)
            let createSuccess = fileManager.createFile(atPath: file.path(), contents: data, attributes: nil)
            print("文件创建结果: \(createSuccess)")
        }
    }
}

```