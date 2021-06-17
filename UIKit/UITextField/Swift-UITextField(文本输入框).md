# Swift-UITextField(文本输入框)

## 文本框的创建，有如下几个样式:

``` swift

UITextBorderStyle.None：无边框
UITextBorderStyle.Line：直线边框
UITextBorderStyle.RoundedRect：圆角矩形边框
UITextBorderStyle.Bezel：边线+阴影

```

``` swift

var  textField =  UITextField (frame:  CGRectMake (10,160,200,30))
//设置边框样式为圆角矩形
textField.borderStyle =  UITextBorderStyle . RoundedRect
self .view.addSubview(textField)

```

## 文本框提示文字

``` swift
	
textField.placeholder= "请输入用户名"

```

## 文字大小超过文本框长度时自动缩小字号,而不是隐藏显示省略号

``` swift

textField.adjustsFontSizeToFitWidth= true   //当文字超出文本框宽度时，自动调整文字大小
textField.minimumFontSize=14   //最小可缩小的字号

```

## 水平/垂直对齐方式

``` swift

/** 水平对齐 **/
textField.textAlignment = . Right  //水平右对齐
textField.textAlignment = . Center  //水平居中对齐
textField.textAlignment = . Left  //水平左对齐
 
/** 垂直对齐 **/
textField.contentVerticalAlignment = . Top   //垂直向上对齐
textField.contentVerticalAlignment = . Center   //垂直居中对齐
textField.contentVerticalAlignment = . Bottom   //垂直向下对齐

```

## 背景图片设置

``` swift

textField.background= UIImage (named: "background1" );

```


## 清除按钮（输入框内右侧小叉）

``` swift

textField.clearButtonMode= UITextFieldViewMode . WhileEditing   //编辑时出现清除按钮
textField.clearButtonMode= UITextFieldViewMode . UnlessEditing   //编辑时不出现，编辑后才出现清除按钮
textField.clearButtonMode= UITextFieldViewMode . Always   //一直显示清除按钮

```

## 使文本框在界面打开时就获取焦点，并弹出输入键盘

``` swift

textField.becomeFirstResponder()

```

## 设置键盘return键的样式

``` swift

textField.returnKeyType =  UIReturnKeyType . Done  //表示完成输入
textField.returnKeyType =  UIReturnKeyType . Go  //表示完成输入，同时会跳到另一页
textField.returnKeyType =  UIReturnKeyType . Search  //表示搜索
textField.returnKeyType =  UIReturnKeyType . Join  //表示注册用户或添加数据
textField.returnKeyType =  UIReturnKeyType . Next  //表示继续下一步
textField.returnKeyType =  UIReturnKeyType . Send  //表示发送

```

## 键盘return键的响应

``` swift

class  ViewController :  UIViewController , UITextFieldDelegate  {
 
     override  func  viewDidLoad() {
         super .viewDidLoad()
 
         var  textField =  UITextField (frame:  CGRectMake (10,160,200,30))
         //设置边框样式为圆角矩形
         textField.borderStyle =  UITextBorderStyle . RoundedRect
         textField.returnKeyType =  UIReturnKeyType . Done      
         textField.delegate= self
         self .view.addSubview(textField)
     }
     
     func  textFieldShouldReturn(textField: UITextField ) ->  Bool
     {
         //收起键盘
         textField.resignFirstResponder()
         //打印出文本框中的值
         println (textField.text)
         return  true ;
     }
}

```