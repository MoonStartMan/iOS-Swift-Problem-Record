# swift分割字符串

例子 "00CI" 分割为 00CI

``` swift

let dataCode = "00CI" //	这里是后端返回带引号的字符串
let indexStart = dataCode.index(after: dataCode.startIndex)
let index = dataCode.index(indexStart, offsetBy: dataCode.count-3)
let newCode = String(dataCode[indexStart...index])

print(newCode) // 00CI

```