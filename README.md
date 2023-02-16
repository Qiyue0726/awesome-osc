# Awesome-OSC
一个基于 [ModernX](https://github.com/cyl0/ModernX) 和 [mpv-osc-modern](https://github.com/maoiscat/mpv-osc-modern/) 的 mpv 播放器的屏幕控制器。
相较于 mpv-osc-modern/ModernX 主要做了以下几点修改：
* 采用 FontAwesome 图标
* 增加部分按钮及相应功能
* 支持底部控制按钮的自定义摆放，通过 osc.conf 配置

![preview1](https://github.com/Qiyue0726/awesome-osc/blob/main/preview/preview1.png)

![preview2](https://github.com/Qiyue0726/awesome-osc/blob/main/preview/preview2.png)

![preview3](https://github.com/Qiyue0726/awesome-osc/blob/main/preview/preview3.png)

> 以上截图的相关配置均已存在于 osc.conf，如果不满意也可以按照自己的喜好摆放，具体的配置项请往下看

# 安装使用
1. 打开你的 mpv 文件夹，Windows 上通常位于 `\%APPDATA%\mpv\`，Linux 和 Mac 位于 `~/.config/mpv/`。如果找不到，可以看看官方文档[Files section](https://mpv.io/manual/master/#files)
Windows 还可以在 mpv 目录中 创建 `portable_config` 文件夹，然后在其中创建 `scripts` 、`scripts` 和 `fonts` 及 `mpv.conf` 等

2. 将字体文件 `Font Awesome 6 Free-Solid-900` 放到 fonts 文件夹中

3. 将脚本 `awesome-osc.lua` 放到 scripts 文件夹中

4. 将脚本配置文件 `osc.conf` 放到 `script-opts` 文件夹中

5. 在 `mpv.conf` 添加以下配置以禁用自带 osc 和开启无边框
```
# 无边框
no-border

# 关闭简易控制面板On Screen Controller(osc)
no-osc
```

> 完成以上步骤后，即可打开视频文件看到相应效果

# 按钮
相较于 mpv-osc-modern 和 ModernX，目前仅增加两个按钮

## backwardAndPrev
* 鼠标左键：快退，可在 osc.conf 中通过 jumpamount 配置快进快退秒数
* 鼠标右键：上一个文件
* shift + 鼠标左键：上一个章节

## forwardAndNext
* 鼠标左键：快进，可在 osc.conf 中通过 jumpamount 配置快进快退秒数
* 鼠标右键：下一个文件
* shift + 鼠标左键：下一个章节

# 自定义配置
mpv-osc-modern 和 ModernX 的配置大部分均可继续使用，目前已知只有配置项 `showjump` 被弃用，但仍可通过配置按钮显示响应的按钮。
主要添加以下配置项：
```
leftBtnArea={'audio','sub'}     # 其值可为：info,fullscreen,audio,sub,play,prev,next,backward,forward,backwardAndPrev,forwardAndNext,jumpback,jumpfrwd,volume,volumeSlider，若该项未配置 play，则该按钮会出现在底部正中间
rightBtnArea={'fullscreen'}     # 其值可为：info,fullscreen,audio,sub,volume,volumeSlider，该项配置需倒序添加
centerBtnAreaL={'prev'}         # 其值可为：prev,backward,jumpback,backwardAndPrev
centerBtnAreaR={'next'}         # 其值可为：next,forward,jumpfrwd,forwardAndNext
playOnTop=yes|no                # 播放时置顶，可配合 SPACE 	cycle pause; cycle ontop 		#空格 切换暂停 等快捷键使用
showFileName=yes|no             # 显示文件名在顶部，若想显示在进度条之上，可使用 showtitle
```
