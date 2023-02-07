# ATS policy have been changed

Xcode报警告解决办法

找到info.plist 添加

``` swift

<key>NSAppTransportSecurity</key>
<dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
</dict>

```