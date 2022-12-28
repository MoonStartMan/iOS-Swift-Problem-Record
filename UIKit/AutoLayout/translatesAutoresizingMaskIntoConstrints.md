# translatesAutoresizingMaskIntoConstrints

+ 把autoresizingMask 转换为 Constraints
+ 即：可以把frame，bounds，center 方式布局的视图自动转化为约束形式。(此时该视图上约束已经足够 不需要手动去添加别的约束)

## 默认值

+ 用代码创建的所有view，translateAutoresizingMaskIntoConstraints默认为true
+ 用XIB创建的所有view，translateAutoresizingMaskIntoConstraints(autoresize布局是true，autolayout布局是false)
+ 视图XIB创建，frame布局，translateAutoresizingMaskIntoConstraints 不用管(XIB帮我们设置好了: true)
+ 视图XIB创建，autolayout布局，translateAutoresizingMaskIntoConstraints 不用管(XIB帮我们设置好了: false)

## 为什么 translatesAutoresizingMaskIntoConstraints 使⽤约束布局时候，就要设置为false

+ translatesAutoresizingMaskIntoConstraints 的本意是将 frame 布局 ⾃动转化为 约束布局，转化的结果是为这个视图⾃动添加所有需要的约束，如果我们这时给视图添加⾃⼰创建的约束就⼀定会约束冲突。
+ 为了避免上⾯说的约束冲突，我们在代码创建 约束布局 的控件时 直接指定这个视图不能⽤frame 布局（即translatesAutoresizingMaskIntoConstraints=false），可以放⼼的去使⽤约束了。