先说说原理吧
警告：要求必须 Android 手机且版本大于等于6.0，无需ROOT，一些通知栏魔改严重的系统可能无法使用。例如MIUI、VIVO。

根据星粉反馈，S8安装后点击多任务按钮会崩，请谨慎使用。楼主S9+没问题。



希望大家好好看看，只有知道了原理才能自行解决一些小错误，更能避免问出一些无脑问题节约大家时间。

首先用到了一个叫 Nevolution 的应用（简称nevo）。

nevo 中文名叫做 女娲石·通知进化，是一个开源通知增强框架，作者就是大名鼎鼎绿色守护的作者。Nevo 可以让一些不思进取的 App 的通知强制适配 Android 的新特性。例如长文本自动换行、多通知合并等。不过它本身并没有什么功能，需要依赖插件实现，类似 Xposed.

其次还需要一个叫做 Android Auto 的应用。

Android Auto 类似苹果的 CarPlay，是谷歌出品的用于连接汽车的应用。借助 Android Auto 的接口，我们可以实现微信回复而无需进入微信应用。

最后我们还需要一个 Nevo-微信 插件，它可以将上面两个连接起来。至此我们实现了通知栏回复微信。接着 Galaxy Watch 自身已经实现了对接 Android 通知栏回复的接口。因此最终我们可以在 Galaxy Watch 上回复微信。

从原始通知栏→新特性适配→回复适配→转到手表，环环相扣，缺一不可。

安装所需应用
警告：要求手机必须是 Android 且大于等于6.0，一些通知栏魔改严重的系统可能无法使用，例如 MIUI、VIVO。

（下面教程大多来自 Nevo Tg 群）

直接安装（不推荐）
为了方便无法连接 Google 的朋友，我把这三个应用都提取了：https://pan.baidu.com/s/1C1mE3D9BTnO7BKSYeBMf8Q 提取码: 77r8

下载后 apk 通过自己喜欢的方式安装在手机上就好了。注意顺序，建议先装 nevolution再装 nevo_wechat 最后安装 Android Auto。

nevo_wechat 安装后是没有启动器图标的，需要卸载可以去手机已安装应用列表找到。

Google Play 安装（推荐）
安装 nevo
由于 Nevo 尚未发布，所以要先加入公测计划。首先点击链接加入 Google+ 社区：https://plus.google.com/communities/108874686073587920040

然后加入 Play Test 计划：https://play.google.com/store/apps/details?id=com.oasisfeng.nevo
（PC 请点击：https://play.google.com/apps/testing/com.oasisfeng.nevo）

等待5-10分钟后即可从 Play 安装。如果提示 您的设备不兼容，在 确定系统版本大于等于6.0的情况下，用浏览器打开：https://play.google.com/store/apps/details?id=com.oasisfeng.nevo 点击安装进行远程推送安装。

安装 nevo-微信
同样先加入测试计划：https://play.google.com/apps/testing/com.oasisfeng.nevo.decorators.wechat

然后即可下载：https://play.google.com/store/apps/details?id=com.oasisfeng.nevo.decorators.wechat

安装 Android Auto
直接搜索安装即可。

进行配置
务必允许 Nevolution 和 nevo-微信 的自启与后台运行

打开 Nevolution 进行配置。这个应用是没有界面的，配置与交互全靠通知栏。首先点击 ACTIVE 激活通知访问权限。在打开的界面中找到 Nevo 并授权。

Galaxy Watch 微信回复 超详细教程
激活通知权限
授权成功后提示 Nevo is ready，点击 CREATE NEW。提示检测到新插件，点击 AVTIVE 激活。

Galaxy Watch 微信回复 超详细教程
创建策略


Galaxy Watch 微信回复 超详细教程
激活插件
此时会自动添加一条微信策略，点击 MODIFY-ADD新增其他策略。

点击 ADD 后会出现三个选项，激活第一个和到三个(Multi-line / Stack)，千万不要激活第二个(No Sitcky)。

Galaxy Watch 微信回复 超详细教程
修改


Galaxy Watch 微信回复 超详细教程
激活新策略
如果错误激活了，可以点击 MODIFY-REMOVE 移除。

OK 到此我们就配置完了。最终为微信激活了三个插件，分别是 微信通知-现代简约风、Multi-line Text、Stack。现在就去试试吧~ 通知栏和手表应该都已经出现回复选项啦。

目前只有微信插件，没有QQ，不要问了。IOS 不能用，也不要问了。

如果没有回复选项，请卸载 Android Auto 和 Nevo-微信，注意安装顺序：先装 nevolution 再装 nevo_wechat 最后安装 Android Auto。

[b]如果手表点击回复提示 请检查手机，那么请试试重启等操作，或者发一个短信回复试试，即可解决这个诡异的问题。[/b]


解决一些小问题
手表微信不震动
打开手机系统的通知设置，找到 Nevo，找到微信类别里的消息类型，点进去后开启震动即可。

Galaxy Watch 微信回复 超详细教程
打开震动
下面是插件作者对于通知的介绍：

关于微信插件的 Notification Channel 功能

目前定义的几个 channel 默认都是没有声音和震动的，因为微信默认开启的声音其实是微信 app 自己在后台播放的，震动也是，而非通过 Android 标准的通知声音/震动机制。所以要为不同的 channel 设置不同的声音和是否震动，就需要：

先在微信里关掉通知声音和震动

长按进化后的微信通知，从那里进入 channel 设置，给不同 channel 设置声音、震动、呼吸灯 等选项。

通知会闪一下
需要 Android 8+

Android 8+ 可以开启 Nevolution 的一个高级模式 —— Assistant 模式，实现通知的无缝替换（不会先闪现一下原通知）及更多特殊功能（比如隐藏划不掉的通知、恢复所有已延后的通知）。开启 Assistant 模式的 ADB shell 指令：

如果是在已 root 手机上的 term 类工具中执行，请先 su（如果遇到 failed transaction 错误，请多执行一次 su）

#[8.0]
settings put secure enabled_notification_assistant com.oasisfeng.nevo/.Assistant

#[8.1+]
cmd notification allow_assistant com.oasisfeng.nevo/.Assistant
（重启后不会失效）

关闭 Assistant 模式的 ADB shell 指令：

#[8.0]
settings delete secure enabled_notification_assistant

#[8.1+]
cmd notification disallow_assistant com.oasisfeng.nevo/.Assistant
通知同步移除
需要 Android 8+

在 ADB shell 中分别执行以下两条指令：

setprop persist.log.tag.NotificationService DEBUG

pm grant com.oasisfeng.nevo android.permission.READ_LOGS
重启设备（不要漏掉这一步）
如果需要关闭，执行第二条指令，将 grant 换成 revoke。

Refer：http://www.galaxyclub.cn/thread-650176-109-147.html
