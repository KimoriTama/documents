---
layout: default
title: ライトユーザー/初心者向け 情報
---

## 文字コードの変換
吉里吉里2ではテキストファイル(*.ks/*.tjs)の文字コードがShift-JISであったため、そのままでは読み込めません(吉里吉里Zでは文字コードがUTF-8になっています)。  
設定を変更することでShift-JISを読み込むようにすることも可能ですが、吉里吉里Zに移行するのであれば、UTF-8に変換してしまった方が良いでしょう。  
変換は、[KanjiTranslator](http://www.kashim.com/kanjitranslator/) がお手軽です。  
起動して、変換先文字コードをUTF-8 (BOM無し)、改行コードはそのままの改行=CR-LFにして、変換するテキストファイル(*.ks/*.tjs)等をドラッグ＆ドロップした後、「変換」ボタンを押せばUTF-8に変換してくれます。  
吉里吉里2と吉里吉里Z両方で使えるようにしたい場合は、UTF-16LE(BOM付き)形式にする必要があります。  
これについては上記ツールでは出来ないので他のツールを探してください。

## 入力補間付きエディタ
吉里吉里2の時は、KKDE/かぐや姫studioなどありましたが、吉里吉里Zでは[KKEFZ](https://github.com/mryp/kkefz)が使えます。  
とりあえずは、[v1.0.0 FD有り版ダウンロード](https://github.com/mryp/kkefz/raw/master/_release/FlashDevelop-4.6.2_kkefz-1.0.0.zip)を選択してダウンロードすると良いでしょう。  
FlashDevelopを既に使っている方はプラグインのみの方問題ないと思います。  

## コンソール
吉里吉里Zではコンソールがなくなり、コマンドラインから起動された場合はコマンドラインへ出力されるようになっています。  
コマンドラインとは、コマンドプロンプト/PowerShellのことです。  
コマンドラインがよくわからない場合は、[Krkr2Compat](https://github.com/krkrz/Krkr2Compat)を導入すると吉里吉里2のようなコンソールを追加できます。 
右にある緑の「Clone or download」ボタンから、Dowonload ZIPを選ぶことでダウンロードできます。  
[ここに同じリンク](https://github.com/krkrz/Krkr2Compat/archive/master.zip)を置いておくので、左述のリンクをクリックしてもダウンロードできます。 
使い方は[00README.txt](https://github.com/krkrz/Krkr2Compat/blob/master/00README.txt)を読んでください。