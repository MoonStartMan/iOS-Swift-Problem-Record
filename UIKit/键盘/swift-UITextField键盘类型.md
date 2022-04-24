# swift-UITextField键盘类型

``` Objective-C

typedef enum {

       UIKeyboardTypeDefault,       默认键盘，支持所有字符

       UIKeyboardTypeASCIICapable,  支持ASCII的默认键盘

       UIKeyboardTypeNumbersAndPunctuation,  标准电话键盘，支持＋＊＃字符

       UIKeyboardTypeURL,            URL键盘，支持.com按钮 只支持URL字符

       UIKeyboardTypeNumberPad,              数字键盘

       UIKeyboardTypePhonePad,    电话键盘

       UIKeyboardTypeNamePhonePad,   电话键盘，也支持输入人名

       UIKeyboardTypeEmailAddress,   用于输入电子 邮件地址的键盘

       UIKeyboardTypeDecimalPad,     数字键盘 有数字和小数点

       UIKeyboardTypeTwitter,        优化的键盘，方便输入@、#字符

       UIKeyboardTypeAlphabet = UIKeyboardTypeASCIICapable,

} UIKeyboardType;

```

## 使用方式

``` swift

let textFiled = UITextFiled()
textField.keyboardType = .numberPad //	数字键盘

```