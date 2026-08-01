本页面介绍了显示器的方方面面，包含HDR介绍、屏幕测试工具等。

# HDR

总教程：[(Reddit) PC HDR gaming starting guide.](https://www.reddit.com/r/OLED_Gaming/comments/1otlr5h/pc_hdr_gaming_starting_guide/)

## Windows设置

推荐将系统升级到Windows 11以获得HDR的最佳体验。

切换HDR/SDR模式的快捷键是 Win + Alt + B

首先要做的事情是Windows HDR 校准，从微软商店下载：[(Microsoft Store) Windows HDR Calibration](https://apps.microsoft.com/detail/9N7F2SM5D1LR?hl=zh-cn&gl=CN&ocid=pdpshare)

Windows HDR 校准的前两步是校准峰值亮度，第三步是黑位（最低亮度），最后一步是饱和度。重点是看结束前它给的示例图片中，高光是否足够亮且有细节层次（也即不过曝）。对于OLED显示器，前两步的峰值亮度直接填显示器的峰值亮度数值（可通过厂家官方页面或评测视频中得知）；第三步的最低亮度直接填0；最后一步的饱和度按喜好调节。如果最终的示例图片中的高光过曝，则填写的峰值亮度稍微降低一些；如果高光不够亮，则填写的峰值亮度稍微增加一些。

## HDR模式下的SDR内容

参考这篇文章：[(TFT Central) Here’s Why You Should Only Enable HDR Mode on Your PC When You Are Viewing HDR Content](https://tftcentral.co.uk/articles/heres-why-you-should-only-enable-hdr-mode-on-your-pc-when-you-are-viewing-hdr-content)

在HDR下看SDR内容，可能会遇到三种问题：过亮/过暗问题、发灰发白问题、颜色暗淡问题。

### SDR纸白亮度（过亮/过暗问题）

外接显示器下，可通过设置中的【系统->屏幕->HDR->SDR内容亮度】来调节HDR下的SDR内容亮度。

这个亮度调节遵循 $y=80+4x$ 公式，其中 $x$ $(0\leq x\leq 100)$ 是滑杆数值， $y$ 是向硬件汇报的SDR纸白亮度(nits)，通常就是物理上真实的纸白亮度（除非超过显示器亮度上限）。可以调节到和平时SDR模式下的相同亮度，来使得开关HDR后的全屏纸白亮度得到统一。

笔记本自带屏幕上，滑杆那里显示为【HDR内容亮度】而非【SDR内容亮度】。

### EOTF曲线（发灰发白问题）

Windows中开启HDR模式时，SDR内容的显示遵循分段sRGB曲线，而非标准的Gamma 2.2曲线。这导致黑位被抬升，原本黑的部分会发灰。

解决方案：[(GitHub) dwm_eotf_rs](github.com/SERGEYDJUM/dwm_eotf_rs)

### 色域（颜色暗淡问题）

开启HDR模式后，会觉得颜色比SDR模式时更暗淡。这是因为，现在的显示器大多是广色域显示器，而SDR内容大多在sRGB色域中，而用户不会主动去开启Windows自动颜色管理或者在显示器端作色域缩限。这就导致sRGB内容被拉伸到显示器的广色域，使得用户平时在SDR模式下看到的颜色其实是过饱和的，而不是真实的。而切换到HDR模式后，一切在BT 2020色域中工作，颜色变得正确了，但用户因为习惯了过饱和的颜色，反而觉得真实的颜色暗淡了。

解决方案：我们需要让在SDR和HDR模式下的颜色显示尽可能统一。有两种方案：
* 【方案1：追求SDR和HDR都准确】HDR模式本来就是准确的，因此只需调整SDR模式。在SDR模式下，要么开启Windows自动颜色管理，方法是通过设置中的【系统->屏幕->颜色管理->自动管理应用的颜色】；要么在显示器端设置色域为sRGB色域。注意，不要两者都做，只能选一种做。
* 【方案2：追求SDR和HDR都过饱和】SDR模式本来就是过饱和的，因此只需调整HDR模式。方法是在HDR下调节饱和度。但要注意，以下方法不仅会影响HDR模式下SDR内容的饱和度，也会同时影响HDR内容的饱和度，会造成HDR内容颜色不准确（但既然你选择了这个方案，可能你本来就连HDR内容都想要过饱和，这可能也是你的目的之一）。
  * 调节全局饱和度：显示器端调节饱和度；或者在Windows HDR校准的最后一步拉高饱和度；或者在Nvidia App中的【系统->颜色】里调节饱和度。
  * 调节视频(HDR内容)饱和度：在开启RTX HDR看视频时，在Nvidia App中的【系统->视频->RTX视频增强->HDR】里可以调节饱和度。
  * 调节游戏(HDR内容)饱和度：可以使用Nvidia滤镜RTX 动态亮丽。同时，ReShade的很多插件都有饱和度选项。专门管控HDR下饱和度的ReShade插件是[ReshadeSimpleHDRShaders](https://github.com/MaxG2D/ReshadeSimpleHDRShaders)下的HDR Saturation，ReShade软件里就有。同时，我自己也写了一个模拟从sRGB扩展到P3色域颜色变化的ReShade插件：[Reshade-HDR-Simulate-Oversaturation](https://github.com/lambdacdm/Reshade-HDR-Simulate-Oversaturation)。这个插件的意义在于模拟了色域变换带来的过饱和的感觉（也就是SDR模式下经历的那种过饱和感），这与单纯拉高饱和度数值并不相同，因为色域扩展时每种颜色的饱和度提升程度是不同的。
 
## HDR游戏

### Renodx, ReShade, Special K

* [Renodx Mods](https://github.com/clshortfuse/renodx/wiki/Mods)
* [ReShade](https://reshade.me/)
* [Special K](https://www.special-k.info/)

### DLSS与AI插帧 

DLSS的模型预设推荐使用预设M与预设L，它们对HDR的光影效果更好。

在同时使用Nvidia的AI插帧（注意这里不是指DLSS帧生成）以及某些自动HDR手段时，如果选项里有选，请选HDR 10而不是scRGB：这是因为scRGB会出现画面出现闪烁、波纹等错误。具体而言，如果你是通过ReShade来进行自动HDR，选择Use HDR10 instead of scRGB。如果还使用了Pumbo的Advanced AutoHDR插件，则需要在Output Color Space中选择HDR10 (BT.2020 PQ)。

## RTX HDR

### 参数调节

参考这篇文章：[(Reddit) RTX HDR — Paper White, Gamma & Reference Settings](https://www.reddit.com/r/nvidia/comments/1b03yfg/rtx_hdr_paper_white_gamma_reference_settings/)

* 峰值亮度：填写显示器的峰值亮度与1000 nits这二者之间的最小值。这是因为Nvidia实现有误：尽管滑块可以调节到1000 nits以上，实际汇报的峰值亮度被锁定到1000 nits的上限。这导致假如调到超过1000 nits的数值，则高于1000 nits的部分会被裁切，使得高光部分细节丢失，也就是过曝。
* 中间灰：按如下公式填写值：中间灰 = 纸白亮度 * $0.5^\gamma$ （中间灰与纸白亮度的单位均为nits，伽马值 $\gamma$ 的标准值为2.2）。如果你想统一RTX HDR内容与SDR内容的纸白亮度，这里的纸白亮度可以设置成之前在Windows设置里调节的SDR内容亮度 $y=80+4x$。
* 对比度：推荐填写25。这是因为，滑杆数值的0表示伽马值为2.0，数值25表示伽马值为2.2，数值50表示伽马值为2.4。而伽马值的标准值为2.2。
* 饱和度：按喜好填写，但要注意数值-25表示中性。

### 性能

RTX HDR 对性能影响较大，解决方案：
* 视频讲解：[(b站) 如何降低RTX HDR的性能损耗](https://www.bilibili.com/video/BV1EVSqYYEAD)
* 资源链接：[NvTrueHDR - RTX HDR for games](https://www.nexusmods.com/site/mods/781?tab=description)

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
