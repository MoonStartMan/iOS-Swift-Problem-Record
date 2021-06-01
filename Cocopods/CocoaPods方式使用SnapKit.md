# CocoaPods方式使用SnapKit

## 初始化

进入工程根目录执行命令，生产Podfile文件

``` vim

pod init

```

## 打开Podfile文件

``` vim

vim Podfile

```

## 编辑

``` vim


# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'
 
target 'Aider' do
  # Comment the next line if you're not using Swift and don't want to use dynamic frameworks
  use_frameworks!
  pod 'SnapKit', '~> 5.0' #增加此行
  # Pods for Aider
 
end

```

## 运行CocoaPods install 命令

``` vim

pod install

```