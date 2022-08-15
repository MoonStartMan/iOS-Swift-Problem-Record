# iOS生命周期

## AppDelegate(应用程序生命周期)

``` swift

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

``` swift

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