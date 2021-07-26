# SwiftUI-设置富文本

``` swift

import SwiftUI

struct ContentView: View {
	
	var body: some View {
		//	新建文本视图
		Text("Interactive")
		//	设置文字的字体颜色为黄色
		.foregroundColor(.yellow)
		//	同时给文字设置加粗的显示效果
		.fontWeight(.heavy)
		//	调用文本视图的加号拓展方法,拼接另一个文本视图,
		//	该拓展方法可以将两个文本视图进行拼接，并返回一个统一的文本视图
		+ Text("tutorials ")
			//	设置文本的字体颜色为橙色
			.foregroundColor(.orange)
			//	删除线
			.strikethrough()
			
		+ Text("for")
			//	设置文字的字体颜色为红色
			.foregroundColor(.red)
			//	倾斜
			.italic()
		
		//	拼接
		+ Text("SwiftUI")
			//	设置文字的字体颜色为紫色
			.foregroundColor(.purple)
			//	下划线
			.underline()
	}
	
}

```