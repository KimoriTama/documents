---
layout: default
title: 工具提示的显示方法
---
 
工具提示是鼠标悬停时显示的简单帮助。
具体用Layer.hint表示的内容。
吉里吉里内称为提示。
在吉里吉里2中根据OS的功能（严格地说是VCL）来显示，但是在吉里吉里Z中为了显示任意层而改变了规格。
另外，鼠标悬停在带有触摸面板的平板设备上是无法显示的，因此必须以其他方式显示鼠标悬停。
## 仕様
* 设置提示后，当光标停止一段时间并到达提示显示时间时，将发生Window.onHintChanged（text:string，x:int，y:int，isshow:bool）事件。
* 鼠标停止时间可由property:Window.hintDelay指定。
默认值为500（毫秒）。
以前是固定值的东西现在可以变更。
* 对要绘制提示的图层启用property:Layer.ignoreHintSensing以忽略提示显示。
* isshow为false，事件出现时隐藏。


这样在onHintChanged中isshow为true时，将提示描绘在最前面的层上，提示层如果设定为忽略鼠标消息，则可以显示与以前相同的显示。

以前，只是标准的枯燥显示，但是由于可以在图层上任意描绘，所以不仅可以用文字，也可以用图像等来表示。

## 样例
{% highlight javascript linenos %}
class MainWindow extends Window {
	var base;
	var layer;
	var hintlayer;

	function MainWindow( width, height ) {
		super.Window();
		setSize( width, height );
		setInnerSize( width, height );

		base = new Layer(this, null);
		base.setSize(width,height);
		base.setSizeToImageSize();
		base.name = "base";
		base.visible = true;

		layer = new Layer(this,base);
		layer.setPos(100,200);
		layer.setSize(100,100);
		layer.setSizeToImageSize();
		layer.colorRect(0,0,100,100,0xff0000,128);
		layer.drawText( 0, 40, "Draw Sample Text", 0xffffff );
		layer.hint = "Show Hint";
		layer.visible = true;

		// Hint Layer
		hintlayer = new Layer(this,base);
		hintlayer.visible = false;
		hintlayer.ignoreHintSensing = true;
		hintlayer.font.height = 14;
		hintlayer.hitThreshold = 256;

		// hintDelay = 500; // default
		// hintDelay = 0; // immediate
		// hintDelay = -1; // never
		// hintDelay = 1000; // slow
	}
	function onHintChanged(text,x,y,isshow) {
		if( isshow ) {
			var w = hintlayer.font.getTextWidth( text ) + 6;
			var h = hintlayer.font.getTextHeight( text ) + 4 + 4;
			hintlayer.setImageSize( w, h );
			hintlayer.setSizeToImageSize();

			if( (x+w) > innerWidth ) { x = innerWidth - w; }
			if( (y+h) > innerHeight ) { y = innerHeight - h; }
			hintlayer.setPos( x, y );

			hintlayer.fillRect( 0, 0, w, h, 0 );
			hintlayer.colorRect( 0, 0, w, h, clInfoBk, 196 );

			hintlayer.colorRect( 0, 0, 1, h, 0xFFFFFF );
			hintlayer.colorRect( 0, 0, w, 1, 0xFFFFFF );
			hintlayer.colorRect( w-1, 0, 1, h, 0xFFFFFF );
			hintlayer.colorRect( 0, h-1, w, 1, 0xFFFFFF );

			hintlayer.drawText( 2, 2, text, clInfoText, 220 );
			hintlayer.visible = true;
		} else {
			hintlayer.visible = false;
		}
	}
}
var win = new MainWindow(640,480);
win.visible = true;
{% endhighlight %}

[ GitHub也有同样的示例。](https://github.com/krkrz/krkrz/blob/master/script/Sample/tooltip/startup.tjs)