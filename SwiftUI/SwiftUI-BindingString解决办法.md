# SwiftUI-Binding<String>解决办法


``` swift

LoginInput(inputTypeValue: .normal, placeHolder: "请输入手机号", loginAccount: "", loginPassword: "")

```

报错内容

```

Cannot convert value of type 'String' to expected argument type 'Binding<String>'

翻译:不能将类型'String'的值转换为预期的参数类型'Binding<String>'

```

解决方法

``` swift

LoginInput(inputTypeValue: .normal, placeHolder: "请输入手机号", loginAccount: .constant(""), loginPassword: .constant(""))

```
