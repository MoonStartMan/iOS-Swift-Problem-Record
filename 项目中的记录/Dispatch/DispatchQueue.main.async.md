# DispatchQueue.main.async

## 不带有DispathQueue.main.async

``` swift

class MyViewController: UIViewController {
	func updateUI() {
		print("update")
	}
	
	override func viewDidLoad() {
		super.viewDidLoad()
		print("before")
		updateUI()
		print("after")
	}
}

```

**输出结果**

```

before
update
after

```

## 带有DispatchQueue.main.async

``` swift

class MyViewController: UIViewController {
    func updateUI() {
        print("update")
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        print("before")
        DispatchQueue.main.async {
            updateUI()
        }
        print("after")
    }
}

```

**输出结果**

```

before
after
update

```
