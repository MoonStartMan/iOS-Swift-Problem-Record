# iOS-GCD

## 什么是GCD

Grand Central Dispatch(强大的中枢调度器),是异步执行任务的技术之一。

## GCD的优势

(1) GCD是苹果公司为多核并行运算提供的解决方案
(2) GCD会自动利用更多的CPU内核(双核、四核等)
(3) GCD会自动管理线程的生命周期(创建线程、调度任务、摧毁线程)
(4) 程序员只需要告诉GCD想要执行什么任务，不需要编写任何线程管理代码

## 任务和队列

GCD中有两个很核心的概念： 任务和队列。
任务：你要执行的操作
队列：用来存放任务

## 执行任务的两种方式

### 同步

在当前线程中执行

### 异步

在另一个线程中进行

### GCD中有两个用来执行任务的函数

1. 用同步的方式执行任务 dispatch_sync(dispatch_queue_t queue, dispatch_block_t block)
2. 用异步的方式执行任务 dispatch_async(dispatch_queue_t queue, dispatch_block_t block)

## 队列的两种类型

串行队列：在一个线程中依次执行(dispatch_sync)
并发队列：多个任务同时执行(开启多个线程同时执行任务)(dispatch_async)

### 同步、异步、串行、并发 说明

  同步和异步决定了能不能开启新线程

- 同步：在当前线程中执行任务，不具备开启新线程的能力
- 异步：在新的线程中执行任务，具备开启新线程的能力

  串行和并行决定了任务的执行形式
  
- 串行：任务依次执行
- 并行：多个任务同时并发执行

  注意：只有在异步的时候开启线程，所以只能在异步的时候并发执行任务。
  
## 获取队列的函数

### 获取串行队列

（1）使用dispatch_queue_create函数创建串行队列

``` swift

dispatch_queue_t queue = dispatch_queue_create("wendingding", NULL); // 创建

```

（2）使用主队列（跟主线程相关联的队列）

``` swift

dispatch_queue_t queue = dispatch_get_main_queue();

```

### 获取并行队列

使用dispatch_get_global_queue函数获得全局的并发队列

``` swift

dispatch_queue_t dispatch_get_global_queue(dispatch_queue_priority_t priority,unsigned long flags); // 此参数暂时无用，用0即可

```

说明：全局并发队列的优先级

``` objective-C

#define DISPATCH_QUEUE_PRIORITY_HIGH 2 // 高
#define DISPATCH_QUEUE_PRIORITY_DEFAULT 0 // 默认（中）
#define DISPATCH_QUEUE_PRIORITY_LOW (-2) // 低
#define DISPATCH_QUEUE_PRIORITY_BACKGROUND INT16_MIN // 后台

```

## swift-GCD

###  主队列

``` swift

///	获取主队列
let mainQueue = DispatchQueue.main

```

### 串行队列

``` swift

let queue = DispatchQueue(label: "串行队列")

```

### 并行队列

``` swift

///	获取全局并发队列
let globalQueue = DispatchQueue.global()

///	第二种
let queue = DispatchQueue(label: "并行队列", attributes: .concurrent)

///	第三种
let concurrentQueue = DispatchQueue(label: "concurrentQueue", qos: .default, attributes: [], autoreleaseFrequency: .inherit, target: nil)

```

#### 创建队列方法参数解释

##### label: 队列名称id

##### qos: (服务质量等级)队列的优先级,如果没有指定值,会使用默认的属性 unspecified(不指定优先级)
- 优先级队列： userInteractive > userInitiated > default > utility > background > unspecified
- 优先级：

``` swift 
public static let userInteractive: DispatchQoS 用户交互 
public static let userInitiated: DispatchQoS 用户发起 
public static letdefault: DispatchQoS 默认优先级 
public static let utility: DispatchQoS 对应oc中的low 低 
public static let background: DispatchQoS 后台 
public static let unspecified: DispatchQoS 不指定优先级
```

##### attributes: 选项集合 包含两个选项

concurrent： 表示队列为并行队列

initiallyInactive： 标识队列中的任务需要手动触发，由队列的activate方法来触发 如果未添加此标识，向队列中添加的任务会自动运行，如果不设置该值 表示创建的是串行队列， 如果希望创建的是并行队列，并且需要手动触发的话，需要添加值 [.concurrent, .initiallyInactive] 如果不需要的话 直接传[]

##### autoreleaseFrequency：类型为枚举类型 用来设置管理任务内对象生命周期的 autorelease pool 的自动释放频率 包含三个类型：

``` swift

inherit  //集成目标队列的该属性
workItem  //跟随每个任务的执行周期进行自动创建和是释放
never  //不会自动创建 autorelease pool 需要自己手动管理

```

##### target： 这个参数设置了队列的目标队列，即队列中的任务运行时实际所在的队列。目标队列最终约束了队列的优先级等属性。

在程序中手动创建的队列最后都指向了系统自带的主队类或全局并发队列

