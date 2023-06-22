---
layout: default
title: 吉里吉里Z本体中被删除功能 
---

即使是从吉里吉里Z本体中被删除的功能，只要加入插件等就可以使用。

## KagParser 类
<!-- 吉里吉里Zリポジトリに同梱されている KAGParser.dll をリンクすると利用可能。 -->
链接吉里吉里Z仓库附带的KAGParser.dll即可使用。
## Menu 类
链接吉里吉里Z仓库附带的menu.dll即可使用。

## Pad 类
链接吉里吉里Z仓库附带的Krkr2Compat即可使用。

## 控制台窗口(Debug.console)
链接吉里吉里Z仓库附带的Krkr2Compat即可使用。

## 脚本编辑器
链接吉里吉里Z仓库附带的Krkr2Compat即可使用。

## 字体选择器(Font.doUserSelect)
链接吉里吉里Z仓库附带的Krkr2Compat即可使用。

## 单行对话框(System.inputString)
链接吉里吉里Z仓库附带的Krkr2Compat即可使用。

## Layer.hint
可通过TJS实现。有关详细信息，请参见[如何显示工具提示](./tooltip.html)。

## Layer 类的 obsolete 方法
affineBlend/affinePile/blendRect/pileRect/stretchBlend/stretchPile方法可以在以下TJS中实现。

{% highlight javascript %}
Layer.affineBlend = function(src, sleft, stop, swidth, sheight, affine, A, B, C, D, E, F, opa=255, type=stNearest) {
    this.operateAffine(src, sleft, stop, swidth, sheight, affine, A, B, C, D, E, F, omOpaque, opa, type);
};
Layer.affinePile = function(src, sleft, stop, swidth, sheight, affine, A, B, C, D, E, F, opa=255, type=stNearest) {
    this.operateAffine(src, sleft, stop, swidth, sheight, affine, A, B, C, D, E, F, omAuto, opa, type);
};
Layer.blendRect = function(dleft, dtop, src, sleft, stop, swidth, sheight, opa=255) {
    this.operateRect(dleft, dtop, src, sleft, stop, swidth, sheight, omOpaque, opa);
};
Layer.pileRect = function(dleft, dtop, src, sleft, stop, swidth, sheight, opa=255) {
    this.operateRect(dleft, dtop, src, sleft, stop, swidth, sheight, omAuto, opa);
};
Layer.stretchBlend = function(dleft, dtop, dwidth, dheight, src, sleft, stop, swidth, sheight, opa=255, type=stNearest) {
    this.operateStretch(dleft, dtop, dwidth, dheight, src, sleft, stop, swidth, sheight, omOpaque, opa, type);
};
Layer.stretchPile = function(dleft, dtop, dwidth, dheight, src, sleft, stop, swidth, sheight, opa=255, type=stNearest) {
    this.operateStretch(dleft, dtop, dwidth, dheight, src, sleft, stop, swidth, sheight, omAuto, opa, type);
};
{% endhighlight %}
