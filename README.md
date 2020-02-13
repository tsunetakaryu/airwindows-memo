# Airwindows 入门指南

## 一、什么是 Airwindows？

Airwindows 是由 Chris Johnson 一人独立开发的一整套音频效果器插件。一开始是付费的，随着其 Patreon 目标达成，他已经逐步放出若干免费插件。其插件的特点是 None-GUI（无图形界面），插件支持格式为 LinuxVST、MacAU、MacVST、WinVST32、WinVST64。

http://www.airwindows.com



## 二、没有 GUI 的 Airwindows

为什么这些插件没有提供 GUI 呢？CJ 的解释有如下两点。

> Airwindows’ reputation was built out of generic-interface plugins, which typically focus on doing only one thing, often with very simple controls, labelled to help understanding but not to encourage formulaic work. There are two reasons for the generic, non-GUI interfaces. One, because it improves reliability a huge amount (many audio plugin bugs, including showstopper bugs, have to do with the GUI part). Two, because time that could be spent debugging the GUI or tweaking its look—or writing copyprotect code—can be better spent improving the sound. That’s how Airwindows rolls, since 2007.
> *来自：[http://www.airwindows.com/vsts/](https://link.zhihu.com/?target=http%3A//www.airwindows.com/vsts/)*

简单来说就是避免了 GUI 产生的各类问题，以及省去了插件开发时 GUI 设计的耗时。

另外，Chris Johnson 也提到他自己的哲理

> in mix, nobody can hear your screen.

笔者深有感触，很多刚入门的音频工作者（甚至是一些前辈）往往会把注意力放到华丽的插件界面上去——他们是在用眼睛混音而不是用耳朵混音。大多数商业插件为了提高产品竞争力而砸钱请设计师设计华丽的产品界面，这确实是一部分原因。但身为从业者，还是不要忘了初心，毕竟模拟味不只是靠一个看上去锈蚀了的青灰色面板就能实现的。

## 三、目前免费的 Airwindows 插件有多少？

大概有一百多个。Chris Johnson 简直是更新狂魔，基本上一周就会出一款新的插件。

另外，笔者与 RCJacH 也在使用 Airwindows 插件，并在 REAPER 群作为平台更新这些插件的汉化版注释（不是汉化插件，因为没这个意义），感兴趣的朋友可以考虑加群学习。

## 四、Airwindows 插件的特色

Airwindows 插件的优势在于失真与抖动算法。

很多商业公司在设计模拟风格的插件时，基本思路是通过 IR 的方法去穷举信号的 IO 响应。比较极端的有意大利的 Acustica Audio，他们将 IR 数据保存为文件让插件读取，一款插件就有 1GB 大小；也有些公司是得到数据之后系统建模，通过数学手段去近似输入输出的关系。

但 Airwindows 不这样做，CJ 的做法是用纯数字的思路去设计失真与抖动（比如 Spiral 插件的失真算法是 `y = sin (x^2)/x`），Gearslutz 上的用户发现，这样的设计与上面的结果几乎没有差距甚至更优。**Deff J** 对照着 Nebula 4 的 IR 预设，在 Desk4 与 Pressure4 中还原了这部分参数。（如果你感兴趣，可以翻翻 GS 上面的贴子后面的评论：https://www.gearslutz.com/board/product-alerts-older-than-2-months/1168113-airwindows-desk4-au-mac-pc-vst.html

## 五、Airwindows 的工作流程

商业插件往往是 All-in-one 的体现，而 Airwindows 的插件更像是将一款硬件的各个模块单独拆分，允许用户自行组合。

我们可以通过 Desk4+Pressure4 的组合来模拟一款硬件压缩器，它可以是 Tube-Tech CL 1B，也可以是 Vari-Mu。在这个效果链里，Desk4 作为前级染色存在，Pressure4 作为压缩模块存在。

## Σ、Airwindowsphobia

- Airwindows 适宜人群：苦行者，效果器穷人，Geek
- Airwindows 不适宜人群：小白，喜欢插件华丽外观糖衣炮弹的混音师，用眼睛混音的大湿，Pro Tools 用户（会很麻烦，因为 PT 的 FX Slots 不够用）

## 附录

Cockos Reaper 讨论群：243473647

Everything About Airwindows：[百度网盘（密码: 9bqi）](https://pan.baidu.com/s/1Qtv5TdhnRhxwDC9_iu399g#list/path=%2F)

下载 Airwindows：[handsewn bespoke digital audio](http://www.airwindows.com)

## 扩展阅读

GS 上面，有人用 SingleEndedTriode 来复刻模拟电路：https://www.gearslutz.com/board/music-computers/1188034-crafting-circuit-models-using-plugins-8.html

