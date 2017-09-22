![logo](https://raw.githubusercontent.com/jcodeing/XMediaGo/master/readme/kmedia_logo.png)

一个为Android打造的应用级媒体框架,它可以助你快速搭建媒体应用.内部重新定义Android MediaPlayer API并对其封装, 简化和扩展一些原生API不支持的功能.
其中涵盖了, `AB播放/循环` `位置单元/间隔/循环` `慢速/快速播放` `媒体队列管理` `媒体服务/绑定` `音频后台通知栏控制` `媒体按键自定义处理` `音频焦点管理` `媒体引擎切换` `第三方媒体引擎扩展`... 等功能的快速实现.
以及, 对视频播放实现方面的封装. 其中将视频视图主要分为:绘制层 控制组 控制层, 三个部分.能够快速并灵活的实现目前视频相关应用的大部分功能,
包括 `视频浮窗/拖动调整位置大小` `竖屏/全屏自动切换` `全屏锁定` `手势调整亮度/音量/进度` `字幕/切换/拖动` `视频段落/间隔复读` `变速` `视频续集/列表/循环播放` `动态切换视频控制层` `控制层分离`... 等功能的快速实现.

## 使用
https://jcodeing.github.io/KMedia-Core/
git submodule add git@github.com:jcodeing/KMedia-Core.git libKMediaCore
git submodule add git@github.com:jcodeing/KMedia-Uie.git libKMediaUie
git submodule add git@github.com:jcodeing/KMedia-Mpe.git libKMediaMpe


git submodule init
git submodule update

framework 采用submodule 方便用户直接将git引入自己的项目 实时同步更新(建议,先fork到自己github 然后将自己的
github/kmediaframework 引入自己的工程做submodule 然后这个submodule再add remove branch->KMediaFramwork)


## 开发
源码辅助阅读:
用google style(->url)
.....
代码style google
https://github.com/google/styleguide/blob/gh-pages/intellij-java-google-style.xml



