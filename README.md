# 狸子的免编译可视化动画模版

隆重推出免编译自适应模版！各种功能正在陆续加入，Flash 可视化交流群：[869200702](http://qm.qq.com/cgi-bin/qm/qr?k=hgiuHM_boX1FmYgsztfpt1Bmw8r7TOcE )


## 模版有以下特性方便新手用户：

- 无需安装 Flash 本体！把数据（和图片）准备好放在同目录下，然后用任意 swf 播放器（`Flash Player`、 `Potplayer`等均可）打开已编译好的 `自适应柱图.swf` 文件即可
- swf 文件已嵌入整套思源黑体字体，因此体积比较大，但免去了新人找字体安装的麻烦
- 对于大跨度的运动采用变速算法，短距离运动切换成匀速运动算法，以此来同时适应跳跃性强的数据和普通数据
- 背景参考系随最大值缩小，但当数据条缩小时不会再放大，以此来同时适应单增的数据和有增有减的数据
- 各种位置、大小、速度参数可通过配置文件调节，只有超出配置文件的内容才需要去修改原工程
- 所有代码从外部加载（`.as` 文件），不必安装 An 也可以研究学习源代码
- 目前包含冠军条、右下冠军大头像等模块，以后会陆续集成更多模块供用户选用


## 你需要做的仅仅是准备数据（和图片）而已，数据格式如下：

- 数据将直接读取同目录下名为 `data.csv` 文件，不需要手动加中括号，字符串也不需要加引号了
- 第一行：第一列填统一后缀（建议 `.png`），从第二列开始是该数据列对应加载图片的名称
- 第二行：从第二列开始是数据列要显示的中文名，不需要加引号了
- 第三行：从第二列开始是每个数据列想显示的颜色
- 从第四行开始是随时间变化的数据，每行第一列是你想要显示的时间字串，每行从第二列开始是各列在该时刻的数据

如果出现乱码：建议将数据文件的编码存为 `UTF-8 with BOM`



## 修改配置文件：

建议用文本编辑器修改 `config.csv`，用 Excel 改有时会吞逗号，然后就炸了 [吐]

- 通过除以分母+前缀+小数位+后缀来调整柱右方显示数字的格式
- 通过检测时间字串中出现某个数段后就截取另一段字串并显示来实现冠军条自动刻度

更多说明见配置文件 `config.csv` 里的注释


<table>
  <tr>
    <td>视频教程</td>
    <td><a href="https://www.bilibili.com/video/av31363620">狸子教你用自动化可视化模版</a></td>
  </tr>
</table>

## 注意：不同版本的 config 文件不能互相兼容，所以我会尽量减少发布的频率（一些内测的版本就只在QQ群里发了）

### 更新日志：

- 2018.09.07
  - 实现加载同目录下配置文件免编译，初版包含冠军条、右下冠军大头像这两个模块
- 2018.09.08 a.1.0
  - 加入对数轴功能，适合量级跨度大还带有伸有缩的数据……
- 2018.09.09 v.0.1
  - 修正了下图标缩小后没对齐的问题
  - 可调参数加了个右端数字距离
- 2018.09.19 v.0.2
  - 加了个柱右端数字限制最大x坐标
  - 背景参考系可设带缓冲系数的回缩
- 2018.09.28 v.0.3
  - 文字加阴影，柱改圆角
  - 冠军头像渐变过渡
  - 把冠军头像宽度设到1920即可实现随冠军切换背景图
- 2018.09.30 v.0.4
  - 冒泡排序法层叠次序反转（最大的显示到最上层）
  - 冒泡排序计算效率改进
- 2018.10.20 v.0.5
  - 可修改背景色，可加载一张背景图并调透明度
  - 可选高亮第几名（结合将柱高度间隔设为负数可实现倒悬排序）
  - 柱图标可加圆遮罩
  - 柱图标、文字可选右对齐
- 2018.10.21 v.0.5.1
  - 可调冠军头像切换渐变速度
- 2018.10.28 v.0.6
  - 可将线性补间调成变速缓冲补间，上升沿斜率越陡踩点越明显
- 2018.11.02 v.0.7
  - 可设置柱子颜色按柱长变色，这种不需要在数据里指定颜色
- 2018.11.04 v.0.8
  - 冠军头像可裁成圆形（配合Ae音频可视化）
  - 选择高亮第几名时亦可选择宽度缩放跟随第几名，兼容数据为负的情况
- 2018.11.08 v.0.8.1
  - 修正最后一列的图片名带个换行符导致图标不能加载的bug
  - 修正一个图标遮罩定位不正确的bug
- 2018.11.13 v.0.8.2
  - 可将数据替换成历史上所有数据的累积
  - 全屏播放下，按空格键可暂停/恢复，按上下左右键可移动柱组
- 2018.11.29 v.0.8.3
  - 读入数据时加了个 NAN 转零的过滤器，数据有空缺时会自动转零
- 2018.12.06
  - 修了个bug（调上下移动速度的分母写错行号了）
- 2018.12.19 v0.8.4 （config.csv 无更改）
  - 启动时冠军头像多检查一次更新
  - 启动时默认为暂停状态，全屏-双击任意文字-按空格才开始播放
- 2018.12.27
  - 柱子的相对y坐标可调
- 2018.12.30 v0.8.5
  - 按上下键平滑移动，移动距离可config
- 2019.03.02 v0.8.5-竖屏
  - 舞台默认尺寸改成1080x1920竖屏，相应加长刻度线，加长文字框长度上限，去掉启动暂停
- 2019.04.05 v0.9
  - merge 了两个 AutoAni-Floater 的功能：
  - 可设置多少帧更新一次排名（减少视觉上柱交换的运动量，强制踩点）
  - 可设置按第一名的数据绘制冠军条高度（这样就是曲线图了）
  - 冠军条加入冠军头像
  - 冠军条可有整体左移速度，这样视觉上时间指针可不运动
- 2019.04.09 v0.9.1
  - 柱子、数字等元素xy都可调
  - 可对某一特定人物加跟踪高亮环
- 2019.07.23 v0.9.2
  - 增加后缀式动态水印功能



对研究原工程感兴趣的可移步 Flash 可视化项目 [FlashAni](https://github.com/LePtC/FlashAni)


<table>
  <tr>
    <td>视频教程（进阶）</td>
    <td><a href="https://www.bilibili.com/video/av29577482">狸子教你用Flash做柱图可视化</a></td>
  </tr>
</table>


有问题建议在 GitHub 上开 issue 问，或者加QQ群：[869200702](http://qm.qq.com/cgi-bin/qm/qr?k=hgiuHM_boX1FmYgsztfpt1Bmw8r7TOcE )


