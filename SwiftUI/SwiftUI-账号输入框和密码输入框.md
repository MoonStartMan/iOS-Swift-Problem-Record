# SwiftUI-账号输入框和密码输入框

## 账号输入框

明文显示的输入框-TextField

``` swift

public init<S>(_ title: S, text: Binding<String>, onEditingChanged: @escaping (Bool) -> Void = { _ in }, onCommit: @escaping () -> Void = {}) where S : StringProtocol

		///		- Parameters:
    ///   - title: The title of the text view, describing its purpose.
    ///   - text: The text to display and edit.
    ///   - onEditingChanged: The action to perform when the user
    ///     begins editing `text` and after the user finishes editing `text`.
    ///     The closure receives a Boolean value that indicates the editing
    ///     status: `true` when the user begins editing, `false` when they
    ///     finish.
    ///   - onCommit: An action to perform when the user performs an action

```

``` swift

TextField("请输入账号", text: .constant("123456")) 
	{ (value) in
	//	code... 输入框变化的时候需要执行的方法
	} onCommit: {
	//	code... 输入完成后需要执行的方法
}

```

## 密码输入框

密文显示的输入框-SecureField

``` swift

public init<S>(_ title: S, text: Binding<String>, onCommit: @escaping () -> Void = {}) where S : StringProtocol

		/// - Parameters:
    ///   - title: The title of `self`, describing its purpose.
    ///   - text: The text to display and edit.
    ///   - onCommit: The action to perform when the user performs an action

```

``` swift

SecureField("请输入密码", text: .constant("123456")) {
	//	code... 密码输入完成后要执行的方法
}

```