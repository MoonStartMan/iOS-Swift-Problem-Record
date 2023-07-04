# RunTime/RunLoop

## RunTime

+ RunTime是Objective-C的核心组成部分之一，它是一种在运行时进行对象消息分发和方法调用的机制。它提供了一套API，允许我们在运行时获取和操作类、实例变量、方法以及消息传递。

+ 在Objective-C中，方法调用是通过消息传递实现的。当我们向一个对象发送消息时，RunTime会根据对象的类结构来查找相应的方法实现，并执行该方法。通过RunTime，我们可以动态地创建、修改类和对象，以及在运行时交换方法实现。

## RunLoop

+ RunLoop是iOS应用程序的事件循环机制。它是一个无限循环，用于处理各种事件，包括用户输入、定时器事件、网络请求等。RunLoop的主要作用是监听和分发事件，确保应用程序能够响应用户的操作，并保持界面的流畅性。

+ RunLoop的工作原理是通过一个事件源和若干个事件处理器组成。事件源负责监听事件的产生，而事件处理器则负责处理事件。当有事件发生时，RunLoop会将事件分发给对应的事件处理器，并执行相应的代码。RunLoop还提供了一些机制，如定时器和触摸事件的分发机制，以便我们能够更好地管理和控制事件的处理。

+ RunLoop在应用程序的主线程中自动启动，并负责处理主线程的事件。它的存在使得我们可以在主线程中执行耗时的操作，同时保持界面的响应性。RunLoop的使用可以帮助我们优化应用程序的性能，并提升用户体验。

## RunTime/RunLoop的Demo

``` swift

import UIKit

class ViewController: UIViewController {

    var timer: Timer?
    
    var currentNum: Int = 0
    
    var isPlay: Bool = false
    
    private var button = UIButton(type: .system)
    
    private var timeLabel: UILabel = UILabel()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        //  创建一个按钮
        button.frame = CGRect(x: 100, y: 100, width: 200, height: 50)
        button.setTitle("Start Timer", for: .normal)
        button.addTarget(self, action: #selector(startTimer), for: .touchUpInside)
        view.addSubview(button)
        
        view.addSubview(timeLabel)
        timeLabel.frame = CGRect(x: 0, y: 150, width: UIScreen.main.bounds.width, height: 40)
        timeLabel.textColor = .black
        timeLabel.font = .systemFont(ofSize: 40, weight: .bold)
        timeLabel.textAlignment = .center
    }

    @objc func startTimer() {
        if !isPlay {
            //  创建一个定时器
            timer = Timer.scheduledTimer(timeInterval: 1.0, target: self, selector: #selector(timerHandler(timer: )), userInfo: nil, repeats: true)
            
            //  将定时器添加到当前RunLoop中,并设置RunLoop的运行模式为默认模式
            RunLoop.current.add(timer!, forMode: .default)
            isPlay = !isPlay
        } else {
            timer?.invalidate()
            timer = nil
            isPlay = !isPlay
        }
        button.setTitle(isPlay ? "Stop Timer" : "Start Timer", for: .normal)
    }

    @objc func timerHandler(timer: Timer) {
        currentNum += 1
        timeLabel.text = "\(currentNum)"
    }
}

```