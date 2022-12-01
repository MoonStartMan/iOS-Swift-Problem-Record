# swift-播放本地音乐

1. 引入```AVFAudio```

``` swift

import UIKit

```

2. 代码部分

``` swift

var player: AVAudioPlayer?

override func viewDidLoad() {
	super.viewDidLoad()
	
	if let soundFilePath = Bundle.main.url(forResource: "music", withExtension: "mp3") {
		player = try? AVAudioPlayer(contentsOf: soundFilePath)
		player?.play()
	}
}

```

