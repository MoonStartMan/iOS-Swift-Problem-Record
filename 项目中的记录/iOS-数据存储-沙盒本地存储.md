# iOS-数据存储-沙盒本地存储

## Documents

1. 保存由应用程序产生的文件或者数据。
2. iCloud会自动备份Documents中的所有文件。
3. 如果保存了网络下载的文件，在上架审批的时候，会被拒。

## Tmp(暂时存放数据，随时回收)

1.临时文件夹，保存临时文件
2.保存在tmp文件夹的文件，系统会自动回收，譬如：磁盘空间紧张或者重新启动手机
3.程序员不需要管tmp文件夹中的释放

## Caches(保存网络下载的数据)

1.缓存，保存从网络下载的文件，后续仍然需要继续使用，例如：网络下载的离线数据，图片，视频…
2.缓存目录中的文件不会自动删除，可以做离线访问
3.要求程序必须提供一个完善的清楚缓存目录的 解决方案

## Preferences(偏好设置)

1.系统偏好，用户偏好
2.操作是通过[NSUserDefaults standardDefaults]来直接操作