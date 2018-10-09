README!!😴 OR-> Read The Fucking 👨‍💻‍Source Code //☀️ 🌧 ⚡️ 🌪 🌫 ❄️...

![logo](/readme/icon/kmedia_logo.svg)

KMedia是一个Android应用级媒体框架,它可以助你快速搭建媒体应用.
内部重新定义Android MediaPlayer API并对其封装, 简化和扩展一些原生API不支持的功能.
其中涵盖了, PlayAB ABLoop PositionUnitLoop PlaybackSpeed MediaQueue PlayerService/Binding
AudioNotifier MediaButtonReceiver AudioFocusManage MultipleMediaEngine... 等功能的快速实现.
以及, 对视频播放实现方面的封装. 其中将视频视图主要分为:SurfaceView ControlGroupView ControlLayerView三个部分.
能够快速并灵活的实现目前视频相关应用的大部分功能, 包括 视频浮窗/拖动调整位置大小 竖屏/全屏自动切换 全屏锁定 手势调整亮度/音量/进度
字幕/切换/拖动 视频段落/间隔复读 变速 视频续集/列表/循环播放 动态切换视频控制层 控制层分离... 等功能的快速实现.

### Usage ###
KMedia framwork can be obtained from JCenter. It's also possible add submodule to your project.

#### From JCenter ####
[![KMedia-Core](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_core.svg)](https://bintray.com/jcodeing/kmedia/kmedia-core/_latestVersion)
[![KMedia-Uie](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_uie.svg)](https://bintray.com/jcodeing/kmedia/kmedia-uie/_latestVersion)
[![KMedia-Exo](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_exo.svg)](https://bintray.com/jcodeing/kmedia/kmedia-exo/_latestVersion)
```gradle
compile 'com.jcodeing:kmedia-core:r1.0.10' //Core module *
compile 'com.jcodeing:kmedia-uie:r1.0.10' //Ui extension module
compile 'com.jcodeing:kmedia-exo:r1.0.10' //Media player extension module
```

#### Add Submodule ####
```command
git submodule add git@github.com:*****/KMedia-Core.git libKMediaCore
git submodule add git@github.com::*****/KMedia-Uie.git libKMediaUie
git submodule add git@github.com::*****/KMedia-Mpe.git libKMediaMpe
```
