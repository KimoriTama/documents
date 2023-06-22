---
layout: default
title: 轻度用户/初学者 信息
---

也请参照[吉里吉里Z 信息](./index.html)。

## 转换字符代码
<!-- 吉里吉里2ではテキストファイル(*.ks/*.tjs)の文字コードがShift-JISであったため、そのままでは読み込めません(吉里吉里Zでは文字コードがUTF-8になっています)。  
設定を変更することでShift-JISを読み込むようにすることも可能ですが、吉里吉里Zに移行するのであれば、UTF-8に変換してしまった方が良いでしょう。  
変換は、[KanjiTranslator](http://www.kashim.com/kanjitranslator/) がお手軽です。  
起動して、変換先文字コードをUTF-8 (BOM無し)、改行コードはそのままの改行=CR-LFにして、変換するテキストファイル(*.ks/*.tjs)等をドラッグ＆ドロップした後、「変換」ボタンを押せばUTF-8に変換してくれます。  
吉里吉里2と吉里吉里Z両方で使えるようにしたい場合は、UTF-16LE(BOM付き)形式にする必要があります。  
これについては上記ツールでは出来ないので他のツールを探してください。 -->
在吉里吉里2中，文本文件（.ks/.tjs）的字符代码为Shift-JIS，因此无法直接读取（在吉里吉里Z中，字符代码为UTF-8）。
您可以通过更改设置来加载Shift-JIS，但如果您要转换为吉里吉里Z，则最好将其转换为UTF-8。
使用[KanjiTranslator](http://www.kashim.com/kanjitranslator/)进行转换非常方便。
启动后，目标字符代码为UTF-8（无BOM），换行代码为CR-LF，拖放要转换的文本文件（.ks/.tjs）等，然后按“转换”按钮将其转换为UTF-8。
如果您想让吉里吉里2和吉里吉里Z都能使用，则必须采用UTF-16LE（带BOM）格式。
关于这个用上述的工具无法使用的话，请找其他的工具。

## 输入补全编辑器
<!-- 吉里吉里2の時は、KKDE/かぐや姫studioなどありましたが、吉里吉里Zでは[KKEFZ](https://github.com/mryp/kkefz)が使えます。  
とりあえずは、[v1.0.0 FD有り版ダウンロード](https://github.com/mryp/kkefz/raw/master/_release/FlashDevelop-4.6.2_kkefz-1.0.0.zip)を選択してダウンロードすると良いでしょう。  
FlashDevelopを既に使っている方はプラグインのみの方問題ないと思います。  
なお、KKEFZに同梱されている吉里吉里Zはバージョンが古いようなので、新しいものへ差し替えた方が良いでしょう。  
 -->
吉里吉里2的时候，有KKDE/辉和姬studio等，吉里吉里Z可以使用[KKEFZ](https://github.com/mryp/kkefz)。
首先，您可以选择下载[v1.0.0 FD版本下载](https://github.com/mryp/kkefz/raw/master/_release/FlashDevelop-4.6.2_kkefz-1.0.zip)。
如果您已经使用了FlashDevelop，我认为只使用插件不会有问题。
再者，KKEFZ附带的吉里吉里Z因为版本似乎较旧，更换新版本较好。

## 控制台
<!-- 吉里吉里Zではコンソールがなくなり、コマンドラインから起動された場合はコマンドラインへ出力されるようになっています。  
コマンドラインとは、コマンドプロンプト/PowerShellのことです。  
コマンドラインがよくわからない場合は、[Krkr2Compat](https://github.com/krkrz/Krkr2Compat)を導入すると吉里吉里2のようなコンソールを追加できます。 
右にある緑の「Clone or download」ボタンから、Dowonload ZIPを選ぶことでダウンロードできます。  
[ここに同じリンク](https://github.com/krkrz/Krkr2Compat/archive/master.zip)を置いておくので、左述のリンクをクリックしてもダウンロードできます。 
使い方は[00README.txt](https://github.com/krkrz/Krkr2Compat/blob/master/00README.txt)を読んでください。   -->
吉里吉里Z没有控制台，如果从命令行启动，则输出到命令行。
命令行是命令提示符/PowerShell。
如果您不了解命令行，则可以通过部署[Krkr2Compat](https://github.com/krkrz/Krkr2Compat)添加一个类似吉里吉里2的控制台。
您可以从右侧绿色的「Clone or download」按钮中选择Dowonload ZIP进行下载。
您可以在[此处](https://github.com/krkrz/Krkr2Compat/archive/master.zip)找到相同的链接，也可以单击下面的链接进行下载。
有关用法，请阅读[00README.txt](https://github.com/krkrz/Krkr2Compat/blob/master/00README.txt)。