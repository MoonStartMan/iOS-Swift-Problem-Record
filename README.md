# iOS-Swift-Problem-Record

<p align="center">
  <img src="https://img.shields.io/badge/Swift-5.0-orange.svg" alt="Swift 5.0">
  <img src="https://img.shields.io/badge/iOS-13.0+-blue.svg" alt="iOS 13.0+">
  <img src="https://img.shields.io/badge/Stars-2-yellow.svg" alt="Stars">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="MIT License">
</p>

<p align="center">
  <b>iOS (Swift) 开发问题记录与解决方案</b>
</p>

## 项目简介

这是一个记录 iOS (Swift) 开发过程中遇到的各种问题及其解决方案的仓库。无论你是 iOS 开发新手还是经验丰富的开发者，这里的问题记录都可能帮助你快速找到解决方案，节省开发时间。

## 问题统计

| 问题类型 | 问题数量 | 状态 |
|---------|---------|------|
| Swift 知识点 | 18 | 持续更新 |
| UIKit | 58 | 持续更新 |
| Cocopods | 1 | 持续更新 |
| Xcode 报错 | 2 | 持续更新 |
| 项目中的记录 | 63 | 持续更新 |
| SwiftUI | 16 | 持续更新 |
| **合计** | **155+** | 持续更新 |

## 内容分类

### Swift 知识点
涵盖 Swift 语言的核心概念和高级特性：

- Swift 中的 `!` 和 `?` 的区别
- `mutating` 关键字的使用
- `where` 关键字
- `typealias` 类型别名
- 协议泛型 `associatedtype`
- `guard` 语法
- 析构过程
- Swift 5 从 0 到 1 创建项目（删除 storyboard）
- `as`、`as!`、`as?` 的区别
- `@escaping` 逃逸闭包
- `stride` 函数
- 墓碑机制与 iOS 应用程序的生命周期
- `NSCalendar` 使用
- GCD 多线程编程
- 数组遍历方法对比
- `propertyWrapper` 属性包装器
- `Encodable` 和 `Decodable`
- `RunTime` 和 `RunLoop`

### UIKit
UIKit 开发中常见的问题和解决方案：

#### UIAlertViewController
- UIAlertViewController 的使用
- 设置标题、内容的字体和颜色

#### AutoLayout
- `translatesAutoresizingMaskIntoConstraints` 详解
- 约束冲突解决

#### 生命周期
- iOS 生命周期详解
- 视图控制器生命周期方法

#### UITableView / UICollectionView
- 数据源和代理方法
- 自定义 Cell
- 性能优化

#### 手势处理
- 添加各种手势识别器
- 手势冲突处理

### Cocopods
- CocoaPods 方式使用 SnapKit
- Podfile 配置
- 常见问题解决

### Xcode 报错
- 常见编译错误解决
- 调试技巧
- 断点使用

### SwiftUI
- SwiftUI 基础组件使用
- 状态管理
- 数据绑定
- 布局系统

## 如何使用

1. **浏览问题**: 根据问题类型进入相应目录
2. **搜索问题**: 使用 GitHub 搜索功能查找特定问题
3. **提交问题**: 如果你遇到了新问题，欢迎提交 Issue 或 PR

## 问题示例

### Swift 中的 ! 和 ? 的区别

```swift
// ? 表示可选类型，值可以为 nil
var optionalName: String? = nil
optionalName = "Hello"

// ! 表示强制解包，如果值为 nil 会崩溃
let forcedName: String = optionalName!

// 安全解包方式
if let safeName = optionalName {
    print(safeName) // 只有不为 nil 时才执行
}

// guard 解包
guard let safeName = optionalName else {
    return
}
```

### 使用 mutating 关键字

```swift
protocol Greetable {
    mutating func greet()
}

struct Person: Greetable {
    var name: String
    
    // struct 是值类型，修改属性需要 mutating
    mutating func greet() {
        name = "Mr. \(name)"
        print("Hello, \(name)")
    }
}
```

## 技术栈

- **编程语言**: Swift 5.0+
- **开发环境**: Xcode 12.0+
- **最低支持系统**: iOS 13.0+
- **框架**: UIKit, SwiftUI, Foundation

## 贡献指南

欢迎贡献你的问题和解决方案！

1. Fork 本仓库
2. 创建你的问题分支 (`git checkout -b add/new-problem`)
3. 添加问题描述和解决方案
4. 提交更改 (`git commit -m 'Add: 问题描述'`)
5. 推送到分支 (`git push origin add/new-problem`)
6. 打开 Pull Request

### 提交规范

- 问题描述清晰
- 提供最小可复现代码
- 给出完整的解决方案
- 如有必要，附上截图

## 项目结构

```
iOS-Swift-Problem-Record/
├── Swift知识点/
│   ├── Swift中的!和的区别.md
│   ├── Swift-mutating关键字.md
│   └── ...
├── UIKit/
│   ├── UIAlertViewController/
│   ├── AutoLayout/
│   └── ...
├── Cocopods/
├── SwiftUI/
├── Xcode报错/
└── README.md
```

## 许可证

本项目采用 MIT 许可证 - 详情请参阅 [LICENSE](LICENSE) 文件

## 致谢

感谢所有为这个项目贡献问题和解决方案的开发者！

## 联系方式

- GitHub: [@MoonStartMan](https://github.com/MoonStartMan)
- 如有问题或建议，欢迎提交 Issue

---

<p align="center">如果这个项目对您有帮助，请给个 ⭐️ 支持一下！<br>让我们一起完善 iOS 开发知识库！</p>
