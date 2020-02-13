# Airwindows 效果器备忘录（使用心得）

## 染色：Console 系统

### Atmosphere [Buss / Channel]、Console 4&5 [Buss / Channel]、PurestConsole [Buss / Channel] 等

> 你可以把加载了任意 ConsoleChannel 的轨道视为虚拟调音台的一个通道，而任意 ConsoleBuss 则是虚拟调音台的最终立体声输出（严格来说不是，这里只是为了方便理解）。
> Console 系统在模仿这样的现象：作为硬件调音台，因为电压或电流的影响，它并不能将复制到两轨的同一个信号通过反相抵消的方式完全静音。且因电信号的相互作用，可能存在类似于套鼓拾音中，各个拾音麦都会相互串音的相互反馈、相互调制现象。
> 为了模仿电信号对音频信号的影响，Console 系统用到了一些精巧的算法，例如 PurestConsole 系列插件，其算法是 Channel 施加 sin (x)，Buss 施加 arcsin (x)。
> 注意这里说的是模仿（Simulate）而不是模拟（Analog Simulate），因为 AW 不是去刻意重建特定硬件设备的特性，只是一些算法在适当的参数组合下 “恰巧” 近似于某些硬件设备的特性。

插件添加的位置：需要**严格遵守**在分轨音频对应的轨道推子后添加 Channel 插件，再到它们的**最高层总线**第一个插槽添加 Buss 插件。例如双轨吉他一左一右有总线，该总线不用添加 Buss 插件。

注意：

- 由于 REAPER 无原生推子前后功能，故应在 Channel 插件之前选择任意一款插件取代 DAW 原生推子与声像电位器，以防止 Console 系统出现计算错误而带来的失真。
- Console5 会**削弱低频**，如果你决定给套鼓与 Bass 使用这套系统，那么得考虑以发送的形式添加 FathomFive 来补充丢失的低频。
- Atmosphere [Buss / Channel] 只用于增强空间感和体积感，如果你希望得到靠前靠上方，明亮、响亮的声音，则需要用其他的插件（例如 Purest Console）。

## **染色：Channel 4&5&6**

共同点：都有三种 SSL（英式）、Neve、API（强瞬态）

不同点：C5 相比 C4 多了输出电平控制，如果将输出设置为 1.0，它将变成旁通状态，此时和 C4 功效一致。C6 则运用了 Spiral 的算法。

## 染色：Desk4

本质上是饱和，可以把它视为任意硬件的染色模块来使用。例如 Desk4 + ReaEQ 这样的组合去模拟一台硬件均衡器。

## 染色：Spiral

算法是 y = sin (x^2)/x．



## 均衡器

### Air

分别对 22K、15K、11K 这三个参数进行扫频找出作用点，如有必要，调整干湿比。

### Bite

增加边缘锋利感，可以配合 Capacitor 使用，后者可以让作用效果不那么过度。

### Enegy

调整方法类似于 Air，这里提供了八个点，处理的频段由高到低（具体的频段是由当前工程采样率决定的）。另外要注意这里针对频率增益量的参数是非线性的。

### Distance & Distance 2

本质是某种形式的倾斜均衡器，模拟距离带来的频段变化。可以解决大部分的 “高频刺耳” 问题，例如套鼓吊顶的高频太燥。需要注意的是 Distance 2 可能会产生直流偏移，需要在该插件后添加一个直流偏移消除插件（例如 REAPER 的 jsfx：DC Filter），否则会影响音频的动态范围。

不要在立体声输出轨使用。

### Slew

可以用它来改变打击乐或踩镲的声音；也可以给乐器或总线添加独特的、有趣的研磨感来将它们变成具有复古的、老派的、垃圾碾压场般的采样器效果；或者为发送式混响添加真实放大器带来的，房间或空间远距离放大声音的感觉。



## 增益

### BitShiftGain

位增益，呈阶梯状改变音量。1Bit 约等于 6.0206dB。

### NC-17

可以用来取代 BSG，但 NC-17 的处理痕迹很重、很脏。



## 动态处理

### ButterComp

想要让素材加一点压缩，那么可以选择这个。如果单纯地把 Compress 参数拉到最右侧，可以把它当做一个 Trimmer。

### HighImpact

瞬态增强处理，引入了失真，例如用来增强底鼓、军鼓的冲击力；增加贝司、节奏吉他的砂砾感。不会影响丰满度。

- 可以将 Output Level 设置到 0.1 的位置，再将 Impact 设置到 1.0，然后逐步提高 Dry/Wet 比例获得理想的效果。
- 或者先将 Output Level 设置到 1.0，再将 D/W 比例设置到 1.0，然后逐步提高 Impact 的量。调节之后可能会 “过量”，这时再将 D/W 调小。

### Point

另一款偏向瞬态处理的压缩工具。Reaction 参数设置在左侧 0.1~0.2 位置时，压缩痕迹与 VCA 压缩器极为相似（尤其是下面的第二个例子）。

需要注意这里的 Point 参数必须慢慢地调整，**用鼠标将它瞬间移动到 1.0 的位置，可能会产生明显的瞬态冲击。**

- 让军鼓推到后方：将 Point 设置到 -1.0，Reaction 设置到大约 0.166 的位置，然后小心地调节 Point 参数来找合适的点。
- 对于整个套鼓，使之平滑的同时想突出镲片声：将 Point 设置到 -1.0，Reaction 设置到大约 0.14 的位置。
- 为了增强底鼓的冲击力，并通过类似门限的方法减少持续时间：先将 Reaction 设置到大约 0.3 的位置，然后小心地调整 Point 数值，直到声音满意为止。

（以上 Point 的使用方法由 [Tiki Horea](https://link.zhihu.com/?target=https%3A//tikihorea.com/) 整理）

### Thunder

又一款瞬态增强，偏向低频处理，原理是保留或增强次声波。例如可以给底鼓增强冲击力。

### Pyewacket

> Chris: Pyewacket is all about retaining the attack transients of things and just stepping on the tails of envelopes.

这款压缩用于保留瞬态的音头（Attack），而处理音尾（Sustain, Tail）的包络。

### Swell

> Chris: Swell is about stomping out those very attack transients until they’re all gone.

这款压缩专门用来抹除所有的瞬态音头。

### Surge

> Chris: Surge is about very smooth gain shifts that are totally transparent and more like an automatic gain control.

非常平滑的增益曲线，近乎完全透明，更像是个自动增益控制。



## 实例

### ElectroHat

可以给 Hi-Hat 素材添加这个插件来抑制机关枪现象，丰富镲片的律动。

### DustBunny、GrooveWear、ToVinyl4

为素材添加黑胶质感。

DustBunny：生成黑胶底噪。

GrooveWear：均衡器，被形容为 “用黑胶指针来机械式地描高频的轮廓”。

ToVinyl4：黑胶母带模拟，饱和，失真。作用有切掉 Side 的低频，或收紧、控制 Mid 的极低频。

### GuitarConditioner

为吉他、电吉他添加特有的失真感，类似于电子管 Screamer。

### uLawDecode、uLawEncode

使用范例为 uLawEncode + 任意效果链 + uLawDecode，uLaw 的组合会将变化部分以失真的形式放大。

------



## 空间

### Wider

通过引入失真（Density 算法），比通过简单调节 Mid/Side 比例的变宽效果器作用更明显。



## 母带或总线处理专用

### Logical4

可以通过反相抵消的方式感受一下 GR 部分来学习这个插件的用法。

你可以从几个方向用 Logical 来完成压缩作业，它有三个截然不同的阶段 ——

- 完全绕过它没有使用的阶段，它将从 1：1 压缩到最多 2：1；
- 只用一个阶段（达到透明度的最大化），将其保持在 2：1 压缩比以下，并使用**阈值**（Threshold）参数控制进行压缩，这是一种传统的总线自然声音压缩；
- 从 2：1 到 4：1 的压缩比，您可以获得各种压缩行为，使用的两个阶段仍然听起来很干净：这时通过**速度**（Speed）参数去精调压缩的行为。
- 然后，当你从 4：1 的比例，并变化到最大值 16：1（近似值）时，音色会发生变化：压缩比越高，Logical 会越疯狂。

（以上的使用方法由 [Tiki Horea](https://link.zhihu.com/?target=https%3A//tikihorea.com/) 整理）

### SurgeTide

总线处理专用版 Surge。

### ToneSlant

超级透明的倾斜均衡器，Q 值非常低。



## 我喜欢的效果链

### Desk4 + ToTape5 + TapeDust

- Desk4 用于模拟磁带机的饱和模块（例如可以选 LineAmp American Tape Recorder 30ips 预设）；
- ToTape5 用于添加 Softer（高频变柔和）、Fatter（低频更丰满）和 Flutter（逆着撸猫，实在不知道怎么形容……RCJacH 说是类似于电流不稳定的状态）三种质感（这三种质感都可以通过反相来听出变化的部分）；
- TapeDust 用来模拟磁带机的调制底噪。