---
layout: default
title: 图像异步读入
---

<!-- 標準の画像読み込みは読み込みを要求した時、その読み込みの完了を待って処理をするが、非同期読み込みでは画像の読み込みをバックグラウンドで行いながら他の処理を出来る。  
このためディスクからの読み込みと言う遅い処理をあまり感じさせないような作りにすることも可能になる。   -->
标准的图像读入在要求读入时，等待读入完成后进行处理，异步读入中，在后台进行图像读入的同时可以进行其他的处理。  
因此，也可以制作成让人无法感觉到从磁盘缓慢的读取的效果。

## 用法
* 使用Bitmap.loadAsync（filename）和Bitmap.onLoaded（meta，async，error，message）进行异步读取。
* 通过loadAsync请求读取，通过onLoaded接收读取完成。
* 通过Bitmap.loading可以判断是否正在异步读取。
* 在异步读取中，如果访问Bitmap的其他成员，就会发生异常。
* 请注意，loadAsync的参数filename包含扩展名，与Layer.loadImages不同，Layer.loadImages可以省略。


### 在 onLoaded 中接收的每个值（meta，async，error，message）如下所示。
* meta : 与Layer.loadImages 返回值相同。标记信息的字典。 
* async : 是否异步读取。使用缓存的情况下，接受请求后直接以onLoaded返回。
* error : 是否发生读取错误。
* message : 错误消息。如果出现错误，则会传递错误消息。

<!-- 読み込んだ画像は Layer.copyFromBitmapToMainImage(Bitmap) によって、Bitmap から Layer にコピーできる。  
コピーと言っても、変更されるまでは共有されているので、一瞬で終わる。  
読込み処理は非同期であるため、読込みが完了した時に、その画像を渡す Layer が既に無効化されている可能性がある。  
onLoaded で他のオブジェクトへアクセスする場合は、無効化されていないか確認した方が良い。  
もしくは、onLoaded が完了するまで無効化されないようにする必要がある。   -->
导入的图像可以通过 Layer.copyFromBitmapToMainImage（Bitmap）从Bitmap复制到Layer。  
虽然说是复制，但在被更改之前还是共享的，一瞬间就结束了。  
由于读取处理是异步的，在读取完成时，传递该图像的Layer有可能已经被无效化。  
用onLoaded访问其他对象时，最好确认是否被无效化。  
或者，需要在onLoaded完成之前不使其无效化。  

## 示例脚本
{% highlight javascript linenos %}
/*  
异步读取iimage0.png ～ image9.png 10次  
*/  
System.setArgument("-contfreq", 60);  
System.graphicCacheLimit = 0;  
// 启用缓存后无意义，将图像缓存关闭   

class Bitmap2Layer extends Bitmap {  
	var target;  
	var tag;  
	function Bitmap2Layer(layer,filename) {  
		super.Bitmap();  
		this.target = layer;
		this.tag = filename;
	}
	function onLoaded(meta,async,error,message) {
		Debug.message("Exit load async:"+async+", error:"+error+", message:"+message);
		if( !error && isvalid(target) ) { // 确认未无效化，因为它是异步的
			target.copyFromBitmapToMainImage(this);
			target.setSizeToImageSize();
		}
	}
};

class MainWindow extends Window {
	var base;
	var layer;
	var layermove;
	var addval;
	var bmps;

	function MainWindow( width, height ) {
		super.Window();
		setSize( width, height );
		setInnerSize( width, height );

		base = new Layer(this, null);
		base.setSize(width,height);
		base.setSizeToImageSize();
		base.name = "base";
		base.visible = true;
		add( base );

		layer = new Layer(this,base);
		layer.setSize(100,100);
		layer.setSizeToImageSize();
		layer.colorRect(0,0,100,100,0x00ff00,128);
		layer.visible = true;
		add( layer );

		layermove = new Layer(this,base);
		layermove.setSize(100,100);
		layermove.setPos(0,height-100);
		layermove.setSizeToImageSize();
		layermove.colorRect(0,0,100,100,0xff0000,128);
		layermove.drawText( 0, 40, "テスト文字列描画", 0xffffff );
		layermove.visible = true;
		add( layermove );

		bmps = new Array();
		for( var j = 0; j < 10; j++ ) {
		for( var i = 0; i < 10; i++ ) {
			var filename = "image"+i+".png";
			var bmp = new Bitmap2Layer(layer,filename);
			bmp.loadAsync(filename);
			bmps.add(bmp);
		}
		}
		add( bmps );

		addval = 1;
		System.addContinuousHandler(onMoveImage);
	}
	function finalize() {
		System.removeContinuousHandler(onMoveImage);
		super.finalize();
	}
	function onMoveImage() {
		layermove.left += addval;
		if( addval > 0 ) {
			if( layermove.left >= (this.width-layermove.width) ) {
				addval = -1;
			}
		} else {
			if( layermove.left <= 0 ) {
				addval = 1;
			}
		}
	}
};

var win = new MainWindow(640,480);
win.visible = true;
{% endhighlight %}

[GitHub也有同样的示例](https://github.com/krkrz/krkrz/blob/master/script/Sample/asyncimageload/startup.tjs)

