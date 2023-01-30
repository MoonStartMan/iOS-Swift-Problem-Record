# swift-Subscript下标的使用

下标脚本允许你通过实例后面的括号中传入一个或者多个的索引值来对实例进行访问和赋值。

下标脚本就是对一个东西通过索引，快速取值的一种语法，例如数组的a[0]。

在swift中，我们可以对类(Class)、结构体(Struct)、枚举(enumeration)中自己定义下标脚本的语法。

## 重点

下标脚本使用subscript关键字来定义。

下标脚本使用get、set来定义读、写属性，并不需要2个属性都有，可以只读，并且读必须有。

定义set属性时，传入的参数默认名称为 newValue。并且newValue的类型和subscript函数返回值相同。

## 代码部分

``` swift

import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        var xiaoli = Student(math: 98, chinese: 97, english: 100)
        print(xiaoli.scoreOf(course: "math"))
        
        xiaoli["math"] = 99
        print(xiaoli["math"])
    }

    
}

struct Student {
    let name: String = ""
    var math: Int = 0
    var chinese: Int = 0
    var english: Int = 0
    
    func scoreOf(course: String) -> Int? {
        switch course {
        case "math":
            return math
        case "chinese":
            return chinese
        case "english":
            return english
        default:
            return nil
        }
    }
    
    subscript (course: String) -> Int? {
        get {
            switch course {
            case "math":
                return math
            case "chinese":
                return chinese
            case "english":
                return english
            default:
                return nil
            }
        }
        set {
            switch course {
            case "math":
                return math = newValue!
            case "chinese":
                return chinese = newValue!
            case "english":
                return english = newValue!
            default:
                print("key wrong")
            }
        }
    }
}

```