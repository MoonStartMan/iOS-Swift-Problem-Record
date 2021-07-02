# swift关键字@escaping

## 逃逸闭包

概念：一个接受闭包作为参数的函数，该闭包可能在函数返回后才被调用，也就是说这个闭包逃离了函数的作用域，这种闭包称为逃逸闭包。当你声明一个接受闭包作为形式参数的函数时，你可以在形式参数前写@escaping来明确闭包是允许逃逸。

例如：当网络请求结束后调用的闭包。发起请求一段时间后这个闭包才执行，并不一定是在函数作用域内执行的。

``` swift

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        getData { (data) in
            print("闭包结果返回--\(data)--\(Thread.current)")
        }
    }
    
    func getData(closure:@escaping (Any) -> Void) {
        print("函数开始执行--\(Thread.current)")
        DispatchQueue.global().async {
            DispatchQueue.main.asyncAfter(deadline: DispatchTime.now()+2, execute: {
                print("执行了闭包---\(Thread.current)")
                closure("345")
            })
        }
        print("函数执行结束---\(Thread.current)")
    }
}

```

逃逸闭包的生命周期:

1、闭包作为参数传递给函数；

2、退出函数；

3、闭包被调用，闭包生命周期结束

即逃逸闭包的生命周期长于函数，函数退出的时候，逃逸闭包的引用仍被其他对象持有，不会在函数结束时释放。

为了管理内存，闭包会强引用它捕获的所有对象，比如你在闭包中访问了当前控制器的属性、函数，编译器会要求你在闭包中显示 self 的引用，这样闭包会持有当前对象，容易导致循环引用。