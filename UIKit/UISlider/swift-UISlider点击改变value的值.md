# swift-UISlider点击改变value的值


``` swift

class ViewController: UIViewController {
	
	var slider: UISlider!
	
	override func viewDidLoad() {
		
		//	Setup the slider
		
		//	Add a gesture recognizer to the slider
		let tapGestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(sliderTapped(gestureRecognizer:)))
        self.slider.addGestureRecognizer(tapGestureRecognizer)
		
		func sliderTapped(gestureRecognizer: UIGestureRecognizer) {
        //  print("A")

        let pointTapped: CGPoint = gestureRecognizer.location(in: self.view)

        let positionOfSlider: CGPoint = slider.frame.origin
        let widthOfSlider: CGFloat = slider.frame.size.width
        let newValue = ((pointTapped.x - positionOfSlider.x) * CGFloat(slider.maximumValue) / widthOfSlider)

        slider.setValue(Float(newValue), animated: true)
    }
	}
}

```