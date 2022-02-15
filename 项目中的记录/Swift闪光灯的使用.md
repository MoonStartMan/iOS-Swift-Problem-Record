# Swift闪光灯的使用

在iOS里面闪光的使用依赖于AVFoundation,并创建具体媒体对象,然后加锁设备、调用、解锁即可。

``` swift

import UIKit
import SnapKit
import AVFoundation

class SecondView: UIViewController {

	//	创建Device实例对象
	let device = AVCaptureDevice.default(for: AVMediaType.video)
	
	let buttonFlashLow = UIButton(type: UIButton.ButtonType.system)
	
	private func initView() {
		buttonFlashLow.setTile("Flash", for: UIControl.State())
		buttonFlashLow.addTarget(self, action: #selector(flashLigh), for: UIControl.Event.touchUpInside)
		buttonFlashLow.snp.makeConstraints { make in
			make.width.equalTo(100)
			make.height.equalTo(60)
		}
	}
	
	override func viewDidLoad() {
		super.viewDidload()
		
		initView()
	}
	
	@objc func flashLight() {
		if device!.hasTorch && ((device?.isTorchAvailable) != nil) {
			//	加锁
			try? device?.lockForConfiguration()
			if device?.torchMode == .off {
				//	开灯
				device?.torchMode = .on
			} else {
				//	关灯
				device?.torchMode = .off
			}
			//	解锁
			device!.unlockForConfiguration()
		}
	}
	
}

```