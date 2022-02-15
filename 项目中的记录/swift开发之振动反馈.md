# swift开发之振动反馈

``` swift

//建立的SystemSoundID对象,标准长震动
let soundID = SystemSoundID(kSystemSoundID_Vibrate)

//短振动，普通短震，3D Touch 中 Peek 震动反馈
let soundShort = SystemSoundID(1519)

//普通短震，3D Touch 中 Pop 震动反馈,home 键的振动
let soundMiddle = SystemSoundID(1520)

// 连续三次短震
let soundThere = SystemSoundID(1521)

//执行震动
AudioServicesPlaySystemSound(soundID)

```