本页面介绍了显示器的方方面面，包含HDR介绍、屏幕测试工具等。

# HDR

## 教程

* [(Reddit) PC HDR gaming starting guide.](https://www.reddit.com/r/OLED_Gaming/comments/1otlr5h/pc_hdr_gaming_starting_guide/)
* [(Reddit) RTX HDR — Paper White, Gamma & Reference Settings](https://www.reddit.com/r/nvidia/comments/1b03yfg/rtx_hdr_paper_white_gamma_reference_settings/)
* [(TFT Central) Here’s Why You Should Only Enable HDR Mode on Your PC When You Are Viewing HDR Content](https://tftcentral.co.uk/articles/heres-why-you-should-only-enable-hdr-mode-on-your-pc-when-you-are-viewing-hdr-content)

## Windows设置

* 切换HDR/SDR快捷键：Win + Alt + B
* Windows HDR 校准：[(Microsoft Store) Windows HDR Calibration](https://apps.microsoft.com/detail/9N7F2SM5D1LR?hl=zh-cn&gl=CN&ocid=pdpshare)

Windows HDR校准的前两步是校准峰值亮度，第三步是黑位（最低亮度），最后一步是饱和度。

## Renodx, ReShade, Special K

* [Renodx Mods](https://github.com/clshortfuse/renodx/wiki/Mods)
* [ReShade](https://reshade.me/)
* [Special K](https://www.special-k.info/)

## HDR下SDR内容

在HDR下看SDR内容，可能会遇到三种问题：过亮/过暗问题、发灰发白问题、颜色暗淡问题。

### SDR纸白亮度（过亮/过暗问题）

外接显示器下，可通过【系统->屏幕->HDR->SDR内容亮度】来调节HDR下的SDR内容亮度。

这个亮度调节遵循 $y=80+4x$ 公式，其中 $x$ $(0\leq x\leq 100)$ 是滑杆数值， $y$ 是向硬件汇报的绝对亮度(nits)，通常就是物理上的真实亮度（除非超过显示器亮度上限）。可以调节到和平时SDR下的相同亮度，来使得开关HDR后的全屏纸白亮度得到统一。

笔记本自带屏幕上，滑杆那里显示为【HDR内容亮度】而非【SDR内容亮度】。

### EOTF曲线（发灰发白问题）

Windows中开启HDR模式时，SDR内容的显示遵循分段sRGB曲线，而非标准的Gamma 2.2曲线。这导致黑位被抬升，原本黑的部分会发灰。

解决方案：[(GitHub) dwm_eotf_rs](github.com/SERGEYDJUM/dwm_eotf_rs)

### 色域（颜色暗淡问题）





## 截图

HDR下，推荐使用Xbox的工具来截图，快捷键是 Alt + Win + Printscreen ，默认保存在【视频->摄像】里。HDR下会生成两张图片，png格式的和jxr格式的。SDR下只会生成一张png格式的图片。

HDR下，也可使用Windows的截图工具截图，快捷键是 Printscreen 或 Win + Shift + S（截区域），以及 Win + Printscreen（截全屏），默认保存在【图片->屏幕截图】里。但HDR下截图，需要在截图工具的【设置->截图->HDR屏幕截图颜色更正器】打开这个选项，否则画面过曝。

HDR下，还可以使用 Special K Image Viewer 来分析图片的亮度、色域等信息。

# 屏幕测试/工具

## 坏点与通用检测

* [在线屏幕检测](https://screen.bmcx.com/#welcome)

## 黑阶、灰阶、白阶 

* [Black level, The Lagom LCD monitor test pages](http://www.lagom.nl/lcd-test/black.php)
* [(Youtube) Black Level Screen Monitor TV Test Pattern](https://www.youtube.com/watch?v=fv6T7aHsd54)
* [(Youtube) White Level Screen Monitor TV Test Pattern](https://www.youtube.com/watch?v=VJDVvYC0-aU)
* [(Youtube) OLED Uniformity and Greyscale Test](https://www.youtube.com/watch?v=_XHeUH1aY6E)

## HDR

### 参数
* [(Youtube) HDR TEST DISPLAY 0.4 to 1000 nits](https://www.youtube.com/watch?v=j0j-40NrGGU)
* [(b站) HDR 0.4 to 1000nits亮度测试](https://www.bilibili.com/video/BV1RG4y1G7Tb)
* [(Youtube) Black Clipping 4k UHD HDR 10 Calibration](https://www.youtube.com/watch?v=fAhxR-gMU_U)
* [(Youtube) White Clipping 4K UHD HDR 10 T.V. Calibration](https://www.youtube.com/watch?v=_XRbTQk45vQ)

### 实景
* [(Youtube) Honey](https://www.youtube.com/watch?v=njX2bu-_Vw4)
* [(Youtube) Las Vegas](https://www.youtube.com/watch?v=8MCFqGnYW4M&t=3s)
* [(Youtube) Reptiles & Amphibians](https://www.youtube.com/watch?v=9QgT6ZIoXN8)

## 色域

* [Interactive Iamge Comparison](https://webkit.org/blog-files/color-gamut/comparison.html)

## 刷新率、帧率

* [TestUFO](https://testufo.com/)
* [(b站) memc/动态补偿/实时插帧 测试视频](https://www.bilibili.com/video/BV1EZ4y1w7Vj)




# 插帧
