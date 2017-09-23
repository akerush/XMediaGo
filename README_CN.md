![KMedia-Logo](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_logo.svg)

一个为Android打造的应用级媒体框架,它可以助你快速搭建媒体应用.内部重新定义Android MediaPlayer API并对其封装, 简化和扩展一些原生API不支持的功能.
其中涵盖了, `AB播放/循环` `位置单元/间隔/循环` `变速播放` `媒体队列管理` `媒体服务/绑定` `音频后台/通知栏控制` `媒体按键自定义处理` `音频焦点管理` `媒体引擎切换/扩展`... 等功能的快速实现.
以及, 对视频播放实现方面的封装. 其中将视频视图主要分为:绘制层 控制组 控制层, 三个部分. 能够快速并灵活的实现目前视频相关应用的大部分功能,
包括 `视频浮窗/拖动/调整位置大小` `竖屏/全屏自动切换` `全屏锁定` `手势调整亮度/音量/进度` `字幕/切换/拖动` `视频段落/间隔复读` `视频续集/列表/循环播放` `动态切换视频控制层` `控制层分离`... 等功能的快速实现.

## 使用
KMedia框架可以直接从JCenter添加依赖, 或者以子模块的形式添加到工程后再依赖.

### 从JCenter添加依赖 `快捷`
[![KMedia-Core](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_core_release.svg)](https://bintray.com/jcodeing/kmedia/kmedia-core/_latestVersion) [![KMedia-Uie](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_uie_release.svg)](https://bintray.com/jcodeing/kmedia/kmedia-uie/_latestVersion) [![KMedia-Exo](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_exo_release.svg)](https://bintray.com/jcodeing/kmedia/kmedia-exo/_latestVersion)
```gradle
compile 'com.jcodeing:kmedia-core:r1.0.10' //核心模块
compile 'com.jcodeing:kmedia-uie:r1.0.10' //界面扩展模块 (可选)
compile 'com.jcodeing:kmedia-exo:r1.0.10' //媒体引擎扩展模块 (可选)
```

### 添加Submodule到工程后依赖 `自定义强`
[![KMedia-Core-Fork](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_core_fork.svg)](https://github.com/jcodeing/KMedia-Core/fork) [![KMedia-Uie-Fork](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_uie_fork.svg)](https://github.com/jcodeing/KMedia-Uie/fork) [![KMedia-Exo-Fork](https://github.com/jcodeing/XMediaGo/blob/master/readme/icon/kmedia_exo_fork.svg)](https://github.com/jcodeing/KMedia-Exo/fork)

#### Step 1: Fork(↑)模块仓库到你的Github.

#### Step 2: 在你工程的根目录, 用 `git` 命令添加子模块.
```sh
git submodule add git@github.com:*user*/KMedia-Core.git kmedia-core //核心模块
git submodule add git@github.com::*user*/KMedia-Uie.git kmedia-uie //界面扩展模块 (可选)
git submodule add git@github.com::*user*/KMedia-Mpe.git kmedia-mpe //媒体引擎扩展模块 (可选)
```

#### Step 3: 根据上面所添加的子模块配置你工程的 `settings.gradle` 文件.
```gradle
include ':kmedia-core'
include ':kmedia-uie'
include ':exo'
project(':exo').projectDir = new File(settingsDir, 'mpe/exo')
```

#### Step 4: 经过上面的添加配置步骤后, 你就可以在本地依赖并随时开发自定义KMedia的各个模块.
```gradle
compile project(':kmedia-core')
compile project(':kmedia-uie')
compile project(':kmedia-exo')
```

### 演示
![Demo-Screen-Record-1](https://raw.githubusercontent.com/jcodeing/XMediaGo/master/readme/demo_sr_1.gif)
![Demo-Ui](https://raw.githubusercontent.com/jcodeing/XMediaGo/master/readme/demo_ui.gif)
![Demo-Screen-Record-2](https://raw.githubusercontent.com/jcodeing/XMediaGo/master/readme/demo_sr_2.gif)

#### Example 1: 简单的视频播放
首先在Layout中添加PlayerView
```xml
<com.jcodeing.kmedia.video.PlayerView
   android:id="@id/k_player_view"
   android:layout_width="match_parent"
   android:layout_height="200dp"/>
```
然后在Activity中将Player设置给PlayerView即可去播放
```java
Player player = new Player(context).init(new AndroidMediaPlayer());
((PlayerView) findViewById(R.id.k_player_view)).setPlayer(player);
player.play(Uri.parse("video"));
```
最后当你确定不再播放时, 请调用以下方法去释放资源对象
```java
playerView.finish();
player.shutdown();
```

#### Example 2: 简单的视频浮窗
把Player交给VideoFloatingWindowController去显示即可浮屏播放
```java
Player player = new Player(context).init(new ExoMediaPlayer(context));
new VideoFloatingWindowController(getApplicationContext()).show(player);
layer.play(Uri.parse("video"));
```
最后当你确定不再播放时, 请调用以下方法去释放资源对象
```java
player.shutdown();
vFloatingWinControler.hide();
```

#### Example 3: 简单的视频全屏
首先在AndroidManifest文件中, 添加configChanges 到你的Activity
```xml
<activity
  android:configChanges="orientation|keyboardHidden|screenLayout|screenSize"
</activity>
```
然后在Activity中覆写onConfigurationChanged, 并在方法内处理竖屏/全屏切换时需要隐藏和显示的View
```java
@Override
public void onConfigurationChanged(Configuration newConfig) {
  super.onConfigurationChanged(newConfig);
  //Dispose view in control layer switch
  if (newConfig.orientation == Configuration.ORIENTATION_LANDSCAPE) {
    other.setVisibility(View.GONE);
  } else if (newConfig.orientation == Configuration.ORIENTATION_PORTRAIT) {
    other.setVisibility(View.VISIBLE);
  }
}
```
最后调用playerView启用方向助手即可实现简单的横竖屏自动切换.
```java
playerView.setOrientationHelper(this, 1);//enable sensor
```

#### Example X: 更多例子请参考KMedia-Demo

### 文档
https://jcodeing.github.io/KMedia-Core/

### 注意
权限
maven 仓库 google
21低版本 svg

### 开发
git clone https://github.com/jcodeing/KMedia.git

git submodule init
git submodule update

framework 采用submodule 方便用户直接将git引入自己的项目 实时同步更新(建议,先fork到自己github 然后将自己的
github/kmediaframework 引入自己的工程做submodule 然后这个submodule再add remove branch->KMediaFramwork)


源码辅助阅读:
用google style(->url)
.....
代码style google
https://github.com/google/styleguide/blob/gh-pages/intellij-java-google-style.xml
