# iOS生命周期

## AppDelegate(应用程序生命周期)

``` objective-C

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    NSLog(@"应用程序启动");
    return YES;
}

- (void)applicationWillResignActive:(UIApplication *)application {
	NSLog(@"即将从前台进入后台")
}

- (void)applicationDidEnterBackground:(UIApplication *)application
{
    NSLog(@"已经从前台进入后台");
}

- (void)applicationWillEnterForeground:(UIApplication *)application
{
    NSLog(@"即将从后台进入前台");
}

- (void)applicationDidBecomeActive:(UIApplication *)application
{
    NSLog(@"已经从后台进入前台");
}

- (void)applicationWillTerminate:(UIApplication *)application
{
    NSLog(@"应用程序被杀死或关闭");
}

```

## UIViewController(控制器生命周期)

``` objective-C

- (instancetype)init{
    if (self = [super init]) {
        NSLog(@"1.init初始化");
    }
    return self;
}
//当时xib加载时
- (void)awakeFromNib{
    [super awakeFromNib];
    NSLog(@"2.Nib加载成功");
}
- (void)loadView{
    [super loadView];
    NSLog(@"3.加载view。");
}
- (void)viewDidLoad {
    [super viewDidLoad];
    NSLog(@"4.载入完成，可以进行自定义数据以及动态创建其他控件");
}
- (void)viewWillAppear:(BOOL)animated{
    [super viewWillAppear:animated];
    NSLog(@"5.视图将出现在屏幕之前");
}
- (void)viewWillLayoutSubviews{
    [super viewWillLayoutSubviews];
    NSLog(@"6.将要对子视图进行调整");
}
- (void)viewDidLayoutSubviews{
    [super viewDidLayoutSubviews];
    NSLog(@"7.对子视图进行调整完毕");
}
- (void)viewDidAppear:(BOOL)animated{
    [super viewDidAppear:animated];
    NSLog(@"8.视图已在屏幕上渲染完成");
}
- (void)viewWillDisappear:(BOOL)animated{
    [super viewWillDisappear:animated];
    NSLog(@"9.视图将被从屏幕上移除");
}
- (void)viewDidDisappear:(BOOL)animated{
    [super viewDidDisappear:animated];
    NSLog(@"10.视图已经被从屏幕上移除");
}
- (void)dealloc{
    NSLog(@"11.视图被销毁，此处需要对你在init和viewDidLoad中创建的对象进行释放");
}
- (void)didReceiveMemoryWarning{
    [super didReceiveMemoryWarning];
    NSLog(@"12.内存警告");
}

```

## UIView(view生命周期)

``` objective-C

- (void)didAddSubview:(UIView *)subview{
    [super didAddSubview:subview];
    NSLog(@"1.当视图添加子视图时调用");
}

- (void)willRemoveSubview:(UIView *)subview{
    [super willRemoveSubview:subview];
    NSLog(@"2.当子视图从本视图移除时调用");
}

- (void)willMoveToSuperview:(nullable UIView *)newSuperview{
    [super willMoveToSuperview:newSuperview];
    NSLog(@"3.当视图即将加入父视图时 / 当视图即将从父视图移除时调用");
}

- (void)didMoveToSuperview{
    [super didMoveToSuperview];
    NSLog(@"4.当视图加入父视图时 / 当视图从父视图移除时调用");
}

- (void)willMoveToWindow:(nullable UIWindow *)newWindow{
    [super willMoveToWindow:newWindow];
    NSLog(@"5.当视图即将加入window视图时 / 当视图即将从window视图移除时调用");
}

- (void)didMoveToWindow{
    [super didMoveToWindow];
    NSLog(@"6.当视图加入window视图时 / 当视图从window视图移除时调用");
}

```