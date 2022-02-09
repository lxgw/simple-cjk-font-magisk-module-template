# CJK Font Magisk Module Template <sup>SIMPLE</sup> </br> CJK 字体 Magisk 模块模板 <sup>简易版</sup>

> **重要提醒：**
>
> 刷机、刷入 Magisk 模块可能会导致系统无法正常启动，请在操作前审慎考虑，并建议备份重要数据。因操作不当导致的系统故障（包括卡开机动画、功能异常等）或效果异常与模块模板作者无关。

本项目为 **Magisk 字体模块模板**的 GitHub 发行项目。该模板用于制作 Magisk 字体模块，支持 9 个字重，每个字重各一个 ttf 文件。在安装 Magisk 的手机上，使用该模板制作字体模块并刷入，更换字体或许会更简便。

有关套用模板的介绍和原理，请看：[为 Android 换上任意喜欢的字体，你可以试试这个 Magisk 模块（少数派）](https://sspai.com/post/58049)

## 使用方法

1. 在 [Release](https://github.com/lxgw/simple-cjk-font-magisk-module-template/releases/latest) 界面下载 zip 格式的模块模板 **FontTemplate-Magisk204.zip** *（不要直接选择 Download Zip）* 。
2. 利用压缩软件 *（电脑上如 7-zip，手机上如 MT 管理器）* 打开模块模板包内的 `/system/fonts` 文件夹，向里面添加 ttf 或 otf 格式的字体文件。字体文件的命名按照第 3 步的指示。
3. 要使加入的字体能够正常显示，**字体文件须遵循以下命名规则**：
   - 将字体文件更名为 `fontwx.ttf`，其中 `x` 为表示字重 *（font-weight，字体粗细属性）* 的一位数字（1~9）；
   - **系统正文调用的基准字重（即 Regular 字重）**，`x` 数值为 4，即字体文件名为 `fontw4.ttf` *（如果是单字重字体，建议命名为 `fontw4.ttf` 再加到模块的 `/system/fonts` 目录中）* ；
   - **系统标题文本、加粗文本调用的粗字重（即 Bold 字重）**，`x` 数值为 7，即字体文件名为 `fontw7.ttf`；
   - Light、Medium 字重 `x` 分别为 3 和 5，`x` 越小则字重越细，越大则字重越粗；
   - 本字体模块模板支持 9 个字重。
       | x 值 | 字重（Font-Weight） | 中文名称 |
       | ---- | ------------------- | -------- |
       | 1    | Thin (100)          | 极细     |
       | 2    | UltraLight (200)    | 纤细     |
       | 3    | Light (300)         | 细体     |
       | 4    | Regular (400)       | 常规     |
       | 5    | Medium (500)        | 中等     |
       | 6    | SemiBold (600)      | 次粗     |
       | 7    | Bold (700)          | 粗体     |
       | 8    | ExtraBold (800)     | 特粗     |
       | 9    | Heavy/Black (900)   | 超粗     |
4. 模块根目录的 `module.prop` 用于存放模块信息，如模块的名称、版本号、作者等。
   - `id`：模块的代号，仅可包括**字母、数字及半角符号，不包含空格**。**相同 id 的 Magisk 模块不能共存。**
   - `name`：模块名称，可任意填写。
   - `version`：模块版本，可任意填写。
   - `versionCode`：模块版本代号，必须为整数型数值。该值用于版本比较。
   - `author`：模块作者，可任意填写。
   - `description`：模块描述，可任意填写。
   - 所有文本文件的行尾应以 **Unix 格式** 书写。
5. 使用 Magisk 刷入做好的模块，重启。

## 字重测试

[点击此处进入字重测试](https://font.yukonga.top/) （酷安 [@YuKongA / 原名「余空_YuK」](https://www.coolapk.com/u/680367) 制作提供）

## 注意事项

1. `/system/fonts` 目录内的 **EmptyFont** 为空字体文件，为 Android 默认西文字体 Roboto 的掏空字体，主要提供度量和字重信息，**请勿轻易删除。** *（灵感来自 [极限社区](http://bbs.themex.net) RadarNyan，这个网站已经进不去了。）*
2. `/system/product` 文件夹内的内容用以覆盖类原生 Android 系统内置的 Google Sans 字体，实现所替换字体在类原生 ROM 上的全局覆盖。若想保留原生 ROM 内置的 Google Sans 字体，请将模块内的 `/system/product` 文件夹删除。 *由于目前版本（0.4.3）的 Shamiko 下，使用本模板制作的字体模块会导致排除列表内勾选的应用闪退，经排查为 fonts_customization.xml 的原因，现已将该文件删除，回到旧版模块模板屏蔽 Google Sans 的方式——直接用空字体替换 Google Sans。*
3. `/system/etc/fonts.xml` 为字体配置文件，已经过调整以调用空字体及自定义字体，经本人所持有的两部 Android 手机测试 *(Redmi Note 5, Pixel Expericence 12.0, Android 12; Redmi K20 Pro, crDroid 7.9, Android 11)* 均可正常使用，**理论上**可兼容 Android 12 和 Android 11，**但不保证所有 ROM 均能正常使用**。不同 ROM 调用字体的配置文件可能不同，请参阅下面的 **「兼容性调整」** 。
4. **本模块模板最低支持 Magisk 20.4。**
5. ~~请不要在用过 Magisk Hide 或者 Zygisk 之后的 Android 12 系统刷入本模板制作的任何字体模块，会导致被选中的应用闪退。~~ Android 12 需要使用 24.0 及以上版本的 Magisk，开启 Zygisk，配合 Shamiko 0.2.0 及以上版本，并在 Magisk 中取消「遵守排除列表」勾选，隐藏 ROOT 同时防止排除列表内的应用闪退。
6. 想要更加高级的自定义模板，可参阅 [高级版字体模块模板](https://github.com/lxgw/advanced-cjk-font-magisk-module-template)，可自行搭配西文、中文、日文和韩语字体，同样支持 9 个字重。

## 兼容性调整 <sub>仅供参考</sub>

为了使该模块模板更加适合您的手机，需要对模块模板内的配置文件进行调整：

- **OPPO/一加 ColorOS：** 将 `/system/etc/fonts.xml` 复制到 `/system/system_ext/etc/` 目录并重命名为 `fonts_base.xml`。
- **一加 HydrogenOS 11 及以上版本：** 将 `/system/etc/fonts.xml` 复制到相同文件夹，并重命名为 `fonts_base.xml。`
- **魅族 Flyme：** 将 `/system/etc/fonts.xml` 复制 3 份到相同文件夹，并重命名为以下 3 个文件： `fonts_flyme.xml`、`fonts_inter.xml` 和 `fonts_slate.xml`。
- **小米 MIUI 12.5：** 需刷入 [空字体模块](https://www.coolapk.com/feed/29518682?shareKey=NGU4ODM5Yjk3YjZmNjE4OTNiOTQ~&shareUid=633884&shareFrom=com.coolapk.market_11.4.3)。
- 如有其他设备的兼容性调整，请在 issue 提出。

## 字体模块模板作者

基于 [Petit-Abba](https://github.com/Petit-Abba)（酷安 [@Kotch / 原名「阿巴酱」](https://www.coolapk.com/u/1132618)） 的 [Magisk-Modules-Template-ge20.4](https://github.com/Petit-Abba/Magisk-Modules-Template-ge20.4) 制作。

- **Telegram：** @lxgwtg
- **微信公众号：** 霞鹜 *（ID: lxgwshare）*
- **酷安：** [@落霞孤鹜lxgw](https://www.coolapk.com/u/633884)
- **微博：** [@孤鹜先森](https://weibo.com/6624339726)
- **Email：** calxgw2018@gmail.com srtong2006@126.com lxgw1999@qq.com

