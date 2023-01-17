# iOS-获取进程信息-ProcessInfo

``` swift

print("进程编号 --- \(kProcessInfo.globallyUniqueString)")
        
print("进程包内容 --- \(kProcessInfo.environment)")

print("进程 主机域名 --- \(kProcessInfo.hostName)")

print("进程名称 --- \(kProcessInfo.processName)")

print("进程 ID --- \(kProcessInfo.processName)")

print("进程 系统版本 --- \(kProcessInfo.operatingSystemVersionString)")

print("上次开机 到 现在的时间 --- \(kProcessInfo.systemUptime)")

print("是否开启低电量模式 --- \(kProcessInfo.isLowPowerModeEnabled)")

```