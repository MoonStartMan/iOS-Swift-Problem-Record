# iOS-节流与防抖

## 什么是节流

节流指的是在一段时间内，只允许事件触发一次。当事件频繁触发时，节流可以限制事件的执行次数，以减少资源消耗。列如，当用户连续点击一个按钮时，可以使用节流来确保按钮点击事件只触发一次，避免重复操作。

## 什么是防抖

防抖则是在一段时间内，只允许事件触发一次，但是只有在事件触发后的一段时间内没有再次触发才会执行。当事件频繁触发时，防抖可以确保只有最后一次触发事件会被执行，以避免过多的事件处理。例如，当用户连续输入搜索关键字时，可以使用防抖来确保只在用户停止输入一段时间后才进行搜索操作，减少不必要的网络请求。

## 代码部分

### 封装DispatchSemaphoreWrapper

#### 什么是DispatchSemaphore

DispatchSemaphore是GCD（Grand Central Dispatch）中的一个信号量机制，用于控制并发访问资源的数量。

#### 代码封装

``` swift

struct DispatchSemaphoreWrapper {
    private var lock: DispatchSemaphore
    init(value: Int) {
        self.lock = DispatchSemaphore(value: 1)
    }
    
    func sync(execute: () -> ()) {
        _ = lock.wait(timeout: DispatchTime.distantFuture)
        lock.signal()
        execute()
    }
}

```

DispatchSemaphoreWrapper结构体有一个私有属性lock，它是一个DispatchSemaphore对象。在初始化时，通过传入的value参数创建一个初始值为1的DispatchSemaphore实例，表示只允许一个线程同时访问。

结构体中还定义了一个sync方法，它接受一个闭包参数execute。在sync方法中，首先调用lock的wait方法来等待信号量，使用DispatchTime.distantFuture表示一直等待，直到获取到信号量。wait方法会将信号量的值减1，如果当前值为0，则会阻塞当前线程。

#### 节流代码

``` swift

/// 节流
class Throttle {
    
    private let label: String
    private let interval: TimeInterval
    private let queue: DispatchQueue
    private var workItem: DispatchWorkItem?
    private var lock: DispatchSemaphoreWrapper
    private var lastTime: Date = Date()
    
    /// intervalu: 单位毫秒
    init(label: String = "Debouncer", interval: TimeInterval = 0.5) {
        self.label = label
        self.interval = interval
        self.queue = DispatchQueue(label: label)
        self.lock = DispatchSemaphoreWrapper(value: 1)
    }
    
    func call(_ callback: @escaping (() -> ())) {
        self.lock.sync {
            self.workItem?.cancel()
            self.workItem = DispatchWorkItem { [weak self] in
                self?.lastTime = Date()
                callback()
            }
            if let workItem = self.workItem {
                let new = Date()
                let delay = new.timeIntervalSince1970 - lastTime.timeIntervalSince1970 > interval ? DispatchTimeInterval.milliseconds(0) : DispatchTimeInterval.milliseconds(Int(interval * 1000))
                self.queue.asyncAfter(deadline: .now() + delay, execute: workItem)
            }
        }
    }
    
}

```

#### 防抖代码

``` swift

/// 防抖
class Debouncer {
    
    private let label: String
    private let interval: Int
    private let queue: DispatchQueue
    private var workItem: DispatchWorkItem?
    private var lock: DispatchSemaphoreWrapper
    
    /// interval: 单位毫秒
    init(label: String = "Debouncer", interval: Int = 500) {
        self.label = label
        self.interval = interval
        self.queue = DispatchQueue(label: label)
        self.lock = DispatchSemaphoreWrapper(value: 1)
    }
    
    func call(_ callback: @escaping(() -> ())) {
        self.lock.sync {
            self.workItem?.cancel()
            self.workItem = DispatchWorkItem {
                callback()
            }
            
            if let workItem = self.workItem {
                self.queue.asyncAfter(deadline: .now() + DispatchTimeInterval.microseconds(interval), execute: workItem)
            }
        }
    }
}

```

#### 代码调用

``` swift

class ViewController: UIViewController {

    let throttle = Throttle(label: "123", interval: 0.1)
    let debouncer = Debouncer(label: "123", interval: 2000)
    
    private var slider: UISlider = UISlider()
    
    private var textLabel: UILabel = UILabel()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        setupView()
    }
    
    private func setupView() {
        view.addSubview(slider)
        slider.snp.makeConstraints { make in
            make.left.equalTo(36)
            make.right.equalTo(-36)
            make.centerY.equalToSuperview()
            make.height.equalTo(40)
        }
        slider.addTarget(self, action: #selector(sliderValueChange(sender:)), for: .valueChanged)
        
        view.addSubview(textLabel)
        textLabel.snp.makeConstraints { make in
            make.top.equalTo(slider.snp.bottom).offset(20)
            make.centerX.equalToSuperview()
        }
        textLabel.textAlignment = .left
        textLabel.font = .systemFont(ofSize: 16.0, weight: .bold)
        textLabel.textColor = .black
    }
    
    @objc func sliderValueChange(sender: UISlider) {
        throttle.call { [weak self] in
            DispatchQueue.main.async {
                self?.textLabel.text = "\(sender.value)"
            }
        }
    }
}

```