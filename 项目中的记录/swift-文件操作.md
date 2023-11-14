# swift-文件操作

## 获取Document目录

``` swift

let paths = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)
if let documentsDirectory = paths.first {
	return documentsDirectory
}

```

## 获取Library目录

``` swift

let paths = FileManager.default.urls(for: .libraryDirectory, in: .userDomainMask)
if let libraryDirectory = paths.first {
	return libraryDirectory
}

```

## 根据文件名称获取URL地址

``` swift

func getCacheFilePath(name: String) -> URL? {
  guard let documentDirectory = getLibraryDirectory() else {
    return nil
  }
  return documentDirectory.appendingPathComponent(name)
}

```

## 存储文件

``` swift

func saveH5Preload(data: Data, fileName: String, type: H5PreloadType) {
	if let fileURL = getCacheFilePath(name: type.rawValue) {
		do {
			if !fileManager.fileExists(atPath: fileURL.path) {
				try fileManager.createDirectory(atPath: fileURL.path, withIntermediateDirectories: true, attributes: nil)
				}
				try data.write(to: fileURL.appendingPathComponent(fileName))
					MSLog.debug("H5已保存到本地文件: ---->\(fileURL)")
		} catch {
			MSLog.debug("数据存储失败: \(error)")
		}
	} else {
		MSLog.debug("无法读取文件路径")
	}
}

```

## 读取文件

``` swift

func readH5Preload(fileName: String, type: H5PreloadType) -> Data? {
  if let fileURL = getCacheFilePath(name: type.rawValue) {
    do {
      let data = try Data(contentsOf: fileURL.appendingPathComponent(fileName))
      MSLog.debug("成功从文件加载数据: \(fileURL)")
      return data
    } catch {
      MSLog.debug("加载数据失败: \(error)")
      return nil
    }
  } else {
    MSLog.debug("无法获取文件路径")
    return nil
  }
}

```

## 删除文件

``` swift

func removeH5Preload(fileName: String, type: H5PreloadType) {
  if let fileURL = getCacheFilePath(name: type.rawValue) {
    do {
      let file = fileURL.appendingPathComponent(fileName)
      try fileManager.removeItem(at: file)
      MSLog.debug("\(fileName)文件删除成功")
    } catch {
      MSLog.debug("文件删除失败")
    }
  }
}

```

## 查找文件

``` swift

func findFilePath(fileName: String) -> String? {
  let fileManager = FileManager.default
  let libraryDirectory = fileManager.urls(for: .libraryDirectory, in: .userDomainMask).first
  if let targetDirectory = libraryDirectory?.appendingPathComponent(zipName) {
    do {
      let fileURLs = try fileManager.contentsOfDirectory(at: targetDirectory, includingPropertiesForKeys: nil)
      for fileURL in fileURLs {
        if fileURL.lastPathComponent == fileName {
          return fileURL.path
        }
      }
    } catch {
      print("Error while enumerating files \(targetDirectory.path): \(error.localizedDescription)")
    }
  }
  return nil
}

```